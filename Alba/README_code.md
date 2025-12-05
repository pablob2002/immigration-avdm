
### **Alba Directory**

This directory contains one Jupyter notebook (social_patterns.ipynb) with the following content:

- **SETUP**

    1. Modules

    2. Save Figures

        ⮑ *Conditional*
    
- **STUDY OF THE RENT**

    1. Question: What is the geographical distribution of the rent per capita in the different neighborhoods of Barcelona?

    2. Procedure 

        ⮑ *Data lecture and color map planning (GeoDataFrame and plot function)*

    3. Results 

        ⮑ *Color map of rent per capita in Barcelona neighborhoods*

- **STUDY OF THE POPULATION**

    1. Data Lecture

        ⮑ *Selection of nationality groups (with and without Spain)*

    2. Diversity Calculation

        - Question: Can we measure the diversity of each neighborhood of Barcelona?

        - Procedure

            ⮑ *Simpson's Diversity Index (SDI)* ⭢ *Matrix* ⭢ *DataFrame*

            ⮑ *Color map planning: GeoDataFrame and plot function*

        - Results

            ⮑ *Color map of diversity in Barcelona neighborhoods* (with and without Spain)

        - Conclusions

        - Extra: Time evolution of diversity between 1997 and 2025

            ⮑ *Colormaps*

    3. Similarity Between Neighborhoods

        - Question: Giving some neighborhoods, how similar are them taking into account the share of nationalities (birth places) in each neighborhood?

        - Procedure

            ⮑ *Cosine Similarity Method*

            ⮑ *Eigenvalues and eigenvectors study*

        - Results

            - Including Spain

                ⮑ *Heatmap sorted by SDI and alphabetically*

                ⮑ *Eigenvalues plot and PDF (symlog scale)*

                ⮑ *Heatmap sorted by SDI and alphabetically (substracting higher eigenvalue)*

            - Excluding Spain

                ⮑ *Heatmap sorted by previous SDI (without Spain), new SDI (without Spain) and alphabetically*

                ⮑ *Eigenvalues plot and PDF (symlog scale)*

                ⮑ *Heatmap sorted by previous SDI (without Spain), new SDI (without Spain) and alphabetically (substracting higher eigenvalue)*

- **RELATION BETWEEN RENT AND DIVERSITY**

    1. Question: Is there any relation between the rent of a neighborhood and its diversity?

    2. Procedure

        ⮑ *Data lecture from the previous DataFrames: rent and diversity (of each neighborhood)*

    3. Results

        ⮑ *Scatter plot with a trial fitting model*


Let's now deepen into the **arquitecture behind the code**. Firstly, we need to understand how we read the data in each section and then how we process it to get the desired results.

#### **DATA LECTURE AND PROCESSING**

1. **RENT DATA**

    - **Data Directory**: `./data/indicadores_socioeconomicos/`

    - **Function**: `prepare_gdf_rent(year)`

        - Input: year (int)
        - Output: GeoDataFrame with rent per capita data for the specified year
        - Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'rent_per_capita'

        ⮑ *Firstly, we filter de original DataFrame looking for the column 'concepto' to be equal to 'renta media por persona (€)' and then we select the columns of our interest*. Besides, we rename the columns to match with the GeoDataFrame columns and work in English.

        ⮑ *Secondly, we clean the data and make sure that it has a consistent format (not NaN, etc)* .

        ⮑ *We load the GeoDataFrame of the neighborhoods of Barcelona, clean it, format it and rename (for matching with the rent DataFrame)*.

        ⮑ *Finally, we get a GeoDataFrame by merging the rent DataFrame with the neighborhoods GeoDataFrame*.

        | Field | Description | Type |
        | ----- | ----------- | ----- |
        | District | Name of the district | String |
        | Neighborhood | Name of the neighborhood | String |
        | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system | Geometry |
        | rent_per_capita | Rent per capita value for that neighborhood (in €) | Float |

2. **POPULATION DATA**

    - **Data Directory**: `./data/birthPlaceRegion/` and `./data/birthPlace_spain_v_outside/`

    - **Function**: `lecture_df(year, add_spain)`

        - Input: year (int), add_spain (bool)
        - Output: GeoDataFrame with population data for the specified year, including or excluding Spain
        - Metadata: 'Neighborhood', 'Group' and 'Value'

        ⮑ *Firstly, we read the dataset and select the columns of our interest: 'Birth_Place_Region' and 'Value'*. 

        ⮑ We ignore the sex differenciation and sum the values. Besides, we work with customized nationality groups. In order to do that, we read the second dataset to know the Spanish population and substract it from the total population of 'Europe' of each neighborhood.

        ⮑ *We clean the data and make sure that it has a consistent format (not NaN, etc)*.

        ⮑ *Finally, we get a DataFrame with the population of each nationality group per neighborhood*.  

        | Field | Description | Type |
        | ----- | ----------- | ----- |
        | Neighborhood | Name of the neighborhood | String |
        | Group | Nationality group | String |
        | Value | Population value for the group in that neighborhood | Integer |

    - **Complementary Function**: `dictionary_df(year, add_spain)` 

        - Input: year (int), add_spain (bool)
        - Output: Dictionary with neighborhood names as keys and lists of population
        - Metadata: Metadata: 'Neighborhoods' as keays to access individual DataFrames with 'Group' and 'Value' columns

            ⮑ *We use the previous function to get the DataFrame and then we convert it to a dictionary format*.

    - **GDF Function**: (arquitecture similar to ``prepare_gdf_rent``)

        - `prepare_gdf(lecture_function, add_spain, year)`: generates a GeoDataFrame with the Simpson's Diversity Index (SDI) for each neighborhood of Barcelona for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

            ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), year (int).

            ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'Simpsons_Diversity_Index'.

            | Field | Description | Type |
            | ----- | ----------- | ----- |
            | District | Name of the district | String |
            | Neighborhood | Name of the neighborhood | String |
            | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system  | Geometry |
            | Simpsons_Diversity_Index | Simpson's Diversity Index value for that neighborhood | Float [0,1) |

 

    **PROCESSING THE DATA**


    - **CALCULATIONS FUNCTIONS**

        - `simpsons_diversity_index(df)`

            Given a Dataframe for each neighborhood, it computes the SDI (numerical).

        - `compute_neighborhood_diversity(lecture_function, add_spain, year)`: generates a DataFrame with the Simpson's Diversity Index (SDI) for each neighborhood of Barcelona for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

            ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), year (int).

            ⮑ Metadata: 'Neighborhoods' and 'Simpsons_Diversity_Index'.

            | Field | Description | Type |
            | ----- | ----------- | ----- |
            | Neighborhood | Name of the neighborhood | String |
            | Simpsons_Diversity_Index | Simpson's Diversity Index value for that neighborhood | Float [0,1)|

        - `nationality_proportion_matrix_all(lecture_function, add_spain, year)`: generates a DataFrame with the nationality proportions per neighborhood for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

            ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), year (int).

            ⮑ Metadata: Neighborhoods as rows and Groups as columns.

            | Field | Description | Type |
            | ----- | ----------- | ----- |
            | Neighborhood | Name of the neighborhood | String |
            | Group | Name of the nationality group | String |

            Cells contain the proportion value (float) of that nationality in that neighborhood.

        - Predefined function `cosine_similarity(matrix)` from sklearn.metrics.pairwise.

    - **VISUALIZATION OF THE RESULTS**

        To clarify difference between maps, we use function like `diference_df12(df1, df2)` or `df_difference(lecture_function, add_spain, initial_year, final_year)` or `df_difference_rent(Initial_year, Final_year, cmap = 'inferno')`, which computes the difference between two DataFrames (percentage difference) or two maps from different years.

        To plot the maps, we define particular functions like `plot_difference(lecture_function, add_spain,ax, initial_year, final_year, cmap = 'coolwarm')` or `plot_difference_gdf12(ax, df1, df2, cmap='coolwarm', log_scale = False)`. These functions use the previous DataFrames or GeoDataFrames to create color maps with the desired information. The color bars are done by using ScalarMappable from matplotlib.

        - `prepare_gdf_difference_df12(df1, df2)`: generates a GeoDataFrame with the percentage difference between two GeoDataFrames (df1 and df2) for each neighborhood of Barcelona.

            ⮑ Input: df1 (DataFrame), df2 (DataFrame)

            ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and ''Percentage_Difference'

            | Field | Description | Type |
            | ----- | ----------- | ----- |
            | District | Name of the district | String |
            | Neighborhood | Name of the neighborhood | String |
            | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system |  Geometry |
            | Percentage_Difference | Percentage difference value between df1 and df2 for that neighborhood | Float |

        - `df_difference(lecture_function, add_spain, initial_year, final_year)`: generates a GeoDataFrame with the percentage difference of the SDI between two years for each neighborhood of Barcelona, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

            ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), initial_year (int), final_year (int)

            ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'Diversity_difference'

            | Field | Description | Type |
            | ----- | ----------- | ----- |
            | District | Name of the district | String |
            | Neighborhood | Name of the neighborhood | String |
            | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system |  Geometry |
            | Diversity_difference | Percentage difference value of the SDI between the two years for that neighborhood | Float |



#### **DATA SAVING**

The code includes an option to save the generated figures. If the `save_figs` variable is set to `True`, the code checks if the directory `img/` exists; if not, it creates it. Then, at the end of each plotting section, the figures are saved in this directory with appropriate filenames.

Although not implemented since we did not need to create files for this project, it could be easily implemented by adding a similar conditional saving mechanism after the DataFrame creation sections. In this case, we should use the `to_csv()` method of the pandas DataFrame to save the data in CSV format. 


#### **RESULTS**

**STUDY OF THE RENT**

- `1_rent_per_capita_2022.png`: color map of the rent per capita (income) in the neighborhoods of Barcelona with a colorbar indicating the color scale in scientific notation with a color blindness friendly palette (viridis).

- `1_rent_evolution.png`: plot conformed by 3 subplots in 1x3 axes. The first two subplots are colomaps of the rent per capita in 1997 and 2022, respectively, with a common colorbar again with scientific notation and color blindness friendly palette (viridis). The third subplot is another colormap indicating the percentage of variation of the rent per capita between 1997 and 2022, with its own colorbar and other color blindness friendly palette (coolwarm).

**STUDY OF THE POPULATION**

Diversity Calculation

- `2_simpsons_index_comparison.png`: plot conformed by 2 subplots in 1x2 axes. The first two subplots are colormaps of the Simpson's Diversity Index (SDI) calculated including and excluding Spain as one of the nationalities group, respectively, with a common colorbar with a color blindness friendly palette (viridis). The third subplot is another colormap of the percentage difference between both SDI calculations, with its own colorbar and color blindness friendly palette (coolwarm).

- `2_simpsons_index_comparison_evolution.png`: plot conformed by 6 subplots in 2x3 axes. The first row focuses on the scenario in which Spain is included as one of the nationalitys groups, while the second row focuses on the scenario in which Spain is excluded. On the other hand, the first row contains colormaps of the SDI in 1997 while the second row contains colormaps of the SDI in 2022. This 4 subplots share a common colorbar with a color blindness friendly palette (viridis). The last column contains colormaps of the percentage of variation of the SDI between 1997 and 2022 for both scenarios, again with a common colorbar and color blindness friendly palette (coolwarm).

Similarity Between Neighborhoods (Including Spain)

- `3_1_Spain_similarity_heatmap.png`: plot conformed by 2 subplots in 1x2 axes. Both subplots are heatmaps of the cosine similarity matrix between neighborhoods (neighborhoods vs neighborhoods). Particularly, the first subplot sorts the neighborhoods by the SDI including Spain as one of the nationalities groups, while the second subplot sorts the neighborhoods alphabetically. Both subplots share the same colorbar with a color blindness friendly palette (viridis).

- `3_1_Spain_similarity_eigenvalues.png`: plot conformed by 2 subplots in 1x2 axes. Both subplots are scatter plots of the eigenvalues of the cosine similarity matrix between neighborhoods. Particularly, the first subplot plots directly the list of eigenvalues sorted in descending order and with a symmetric log scale in the y axis, while the second subplot plots the PDF of the eigenvalues.

- `3_1_Spain_similarity_heatmap.png`: same as `3_1_Spain_similarity_heatmap.png`, but now modifying the cosine similarity matrix by substracting the information of the largest eigenvalue and its corresponding eigenvector.

Similarity Between Neighborhoods (Excluding Spain)

- `3_2_no_Spain_similarity_heatmap.png`: plot conformed by 3 subplots in 1x3 axes. All subplots are heatmaps of the cosine similarity matrix between neighborhoods (neighborhoods vs neighborhoods) with different sorting criteria: by SDI (excluding Spain), by SDI (including Spain) (order or the previous case) and alphabetically. All subplots share the same colorbar with a color blindness friendly palette (viridis).

- `3_2_no_Spain_similarity_eigenvalues.png`: same as `3_1_Spain_similarity_eigenvalues.png`, but now for the case excluding Spain.

- `3_2_no_Spain_similarity_heatmap.png`: same as `3_2_no_Spain_similarity_heatmap.png`, but now modifying the cosine similarity matrix by substracting the information of the largest eigenvalue and its corresponding eigenvector.

**RELATION BETWEEN RENT AND DIVERSITY**

- `4_rent_diversity.png`: scatter plot representing the relation between the rent per capita and the SDI (including Spain) for each neighborhood of Barcelona in 2022. The plot includes the an exponential fit line and its confidence interval (95%).












        




        

