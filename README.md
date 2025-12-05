# immigration-avdm
This repository contains all the codes used during the project corresponding to the Analysis and Visualization of Big Data of the Master in Physics of Complex Systems and Biophysics in Universitat de Bareclona. 

## Table of contents
- [Contributors](#contributors)
- [Introduction](#introduction)
- [Data Information](#data-information)
   - [Data sets](#data-sets)
   - [Data storage](#data-storage) 
- [Requirements](#requirements)
   - [Python environment](#python-environment)
   - [Uncode and reformat data](#uncode-and-reformat-data)
- [Code execution](#code-execution)
   - [Alba](#alba-directory)
   - [Ale](#ale-directory)
   - [Pablo](#pablo-directory)
   - [Sara](#sara-directory)
   - [Sergi](#sergi-directory)

## Contributors:

- Pablo Barquín Soria (pablob2002)
- Sara González Basdediós (saragonbas)
- Alba López Rivas (abby-lr-ub)
- Sergi Martínez Galindo (sergi-mg)
- Alejandro Palacios Garrido (aleepg72)

## Introduction
This project consists in a data analysis of the immigration (its characteristics and consequences) in the city of Barcelona, from 1997 to 2025, using different open data sources (specified in the following section). The project is divided in five subprojects, each one corresponding to one of the contributors, which have the objective of analysing different specific aspects of the studied topic.

## Data information

### Data sets

1. **Population by geographical region of birth and sex**  
   <https://opendata-ajuntament.barcelona.cat/data/en/dataset/pad_mdb_lloc-naix-regio_sexe>

   | Field            | Description |
   |------------------|-------------|
   | Data_Referencia  | The reference date for the data point. |
   | Codi_Districte   | Code of the district. |
   | Nom_Districte    | Name of the district. |
   | Codi_Barri       | Code of the neighborhood. |
   | Nom_Barri        | Name of the neighborhood. |
   | Valor            | Number of people (the count). |
   | LLOC_NAIX_REGIO  | Geographical region of birth. |
   | SEXE             | Sex. |

2. **Population by birthplace and sex**  
   <https://opendata-ajuntament.barcelona.cat/data/en/dataset/pad_mdbas_lloc-naix_sexe>

   | Field            | Description |
   |------------------|-------------|
   | Data_Referencia  | Reference Date |
   | Codi_Districte   | District Code |
   | Nom_Districte    | District Name |
   | Codi_Barri       | Neighborhood Code |
   | Nom_Barri        | Neighborhood Name |
   | AEB              | Basic Statistical Area |
   | Seccio_Censal    | Census Section |
   | Valor            | Number of people |
   | LLOC_NAIX        | Place of Birth |
   | SEXE             | Sex |

3. **Population aged 16+ by level of education and birthplace** 
   <https://opendata-ajuntament.barcelona.cat/data/en/dataset/pad_mdb_niv-educa-esta_edat-lloc-naix>

   | Field            | Description |
   |------------------|-------------|
   | Data_Referencia  | Reference date |
   | Codi_Districte   | District code |
   | Nom_Districte    | District name |
   | Codi_Barri       | Neighborhood code |
   | Nom_Barri        | Neighborhood name |
   | Valor            | Number of people |
   | NIV_EDUCA_esta   | Academic degree or qualification |
   | LLOC_NAIX        | Place of birth |

4. **Population aged 16+ by level of education and continent of birth** 
   <https://portaldades.ajuntament.barcelona.cat/es/estadísticas/r8qejecnob>

   | Field               | Description |
   |---------------------|-------------|
   | Territorio          | Neighborhood of Barcelona |
   | Titulación académica| Academic degrees |
   | Continentes         | Continent of birth |
   | Año                 | Year (1997–2025) |

5. **Socioeconomic indicators by neighborhood**  
   <https://www.idescat.cat/pub/?id=ist&n=14075&geo=mun:080193&lang=es>

   | Field                                   | Description |
   |-----------------------------------------|-------------|
   | Neighborhood                            | Neighborhood |
   | Población ocupada (%)                   | Employed population (%) |
   | Trabajadores de baja calificación (%)   | Low-qualified workers (%) |
   | Población con estudios bajos (%)        | Low-education population (%) |
   | Población joven sin estudios postobligatorios (%) | Young people without post-compulsory studies (%) |
   | Extranjeros de países de renta baja o media (%) | Foreigners from low/middle-income countries (%) |
   | Renta media por persona (€)             | Average income per person |

6. **Rates of activity, unemployment and employment by province and sex**
   <https://datos.gob.es/en/catalogo/ea0010587-tasas-de-actividad-paro-y-empleo-por-provincia-y-sexo-epa-identificador-api-72989>

   | Field (Original)  | English Term       | Description |
   |-------------------|--------------------|-------------|
   | Periodo           | Period             | Time period |
   | Provincia         | Province           | Spanish province |
   | Codigo Provincia  | Province Code      | Numerical code |
   | Sexo              | Sex                | Male / Female / Total |
   | Tasa de Actividad | Activity Rate      | % in labor force |
   | Tasa de Paro      | Unemployment Rate  | % unemployed |
   | Tasa de Empleo    | Employment Rate    | % employed |

7. **Dimensions of the data sets of the Municipal Register of inhabitants of the city of Barcelona**
   <https://opendata-ajuntament.barcelona.cat/data/dataset/pad-dimensions>

   | Field | Description |
   | ----- | ----------- |
   | Codi_Dimensio | Identifier for the coded dimension |
   | Desc_Dimensio | Dimension |
   | Codi_Valor | Code associated to the value of the dimension |
   | Desc_Valor_CA | Uncoded value of the dimension (catalan) |
   | Desc_Valor_ES | Uncoded value of the dimension (spanish) |
   | Desc_Valor_EN | Uncoded value of the dimension (english) |

8. **Administrative units of the city of Barcelona**
   <https://opendata-ajuntament.barcelona.cat/data/en/dataset/20170706-districtes-barris>

   - *BarcelonaCiutat_Districtes.csv*

      | Field | Description |
      | ----- | ----------- |
      | Codi_Districte | District identifier |
      | nom_districte | District name |
      | geometria_etrs89 | District geometry in *etrs89* format |
      | geometria_wgs84 | District geometry in *wgs84* format |

   - *BarcelonaCiutat_Barris.csv*

      | Field | Description |
      | ----- | ----------- |
      | codi_Districte | District identifier |
      | nom_districte | District name |
      | codi_barri | Neighborhood identifier |
      | nom_barri | Neighborhood name |
      | geometria_etrs89 | Neighborhood geometry in *etrs89* format |
      | geometria_wgs84 | Neighborhood geometry in *wgs84* format |


### Data storage
All the data corresponding to the original data sets can be found in a Google Drive folder (<https://drive.google.com/drive/u/1/folders/1RcMc1dbqj3XbPj8vlShsVeRvFjJF8vma>). In order to be able to execute the code you have to download the orginal_data folder into your local version of this directory and follow the instructions in the "Uncode and reformat data" section. Apart from that, the Google Drive folder also contains the generated data frames during the developement of the project.

## Requirements

### Python environment
The environment used in this project can be found on the GitHub repository of the course on Analysis and Visualization of Big Data from the University of Barcelona (https://github.com/jvicens/analysis-and-visualization-of-big-data-course). 

Here is a quick installation using conda (and pip for unavailable packages) aimed towards working on VSCode:
```console
conda create --name ub-avbd python=3.12
conda activate ub-avbd
conda config --add channels conda-forge
conda install --file requirements.txt
pip install -r requirements.txt
```

Any extra packages required in specific codes will be explained in their respective directories.

### Uncode and reformat data
Most data from Ajuntament de Barcelona is coded, for example for *Sexe* we have 1 and 2 instead of female and male, although a *.csv* file with all the coded values is also provided. Furthermore, some datasets have an inconsistent column names.

To solve this issues, the code *./Ale/0_reformat_data.ipynb* loads the data located at the main directory of the repository *./data_original/* and generates a new folder on the same level *./data/* which will be used in all of our jupyter notebooks, so it **must be run first**. Unmodified files are also cloned to this new folder for better organization as they are fairly light.

## Code execution
**Note**: most codes reorganized the birth place regions from dataset [1] into a smaller set of representative and culturally similar groups:

| Group abbreviation | Birthplaces from the original dataset |
| ------------------ | ------------------------------------- |
| Africa | Eastern Africa, Middle Africa, Southern Africa, Western Africa |
| NAf-WAs | Northern Africa, Western Asia |
| Latin America | Caribbean, Central America, South America |
| Asia | Southern Asia, South-Eastern Asia, Eastern Asia |
| Europe | Eastern Europe, Northern Europe, Southern Europe |
| NAm-Aus-NZ | Northern America, Australia and New Zealand |


### Alba directory

This directory contains one Jupyter notebook (`social_patterns.ipynb`) with the following content:

1. **SETUP** ⭢ *Modules and save figures option*

2. **STUDY OF THE RENT**

3. **STUDY OF THE POPULATION**

    - Diversity Calculation

    - Similarity Between Neighborhoods

4. **RELATION BETWEEN RENT AND DIVERSITY**


This code will generate a folder inside this directory named `.Alba/img/`, where all the figures produced in the notebook will be saved if the option to save figures is set to True (save_figures = True). The final plots of this study are the following:

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

Although not implemented since we did not need to create files for this project, it could be easily implemented by adding a similar conditional saving mechanism after the DataFrame creation sections. In this case, we should use the `to_csv()` method of the pandas DataFrame to save the data in CSV format. 

The functions used to compute the different analysis are explained in detail in the README.md file located inside the folder directory `immigration-avdm/Alba`. Nevertheless, a brief explanation of the main functions used in this notebook is provided below:

**DataFrames**

- `lecture_df(year, add_spain, level = 'Neighborhood')`: generates a DataFrame with the population data for each neighborhood of Barcelona for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

    ⮑ Input: year (int), add_spain (bool), level (str, default 'Neighborhood').

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | Neighborhood | Name of the neighborhood | String |
    | Group | Nationality group | String |
    | Value | Population value for the group in that neighborhood | Integer |

- `dictionary_df(year, add_spain)`: generates a dictionary with neighborhood names as keys and lists of population for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

    ⮑ Input: year (int), add_spain (bool).

    ⮑ Metadata: Neighborhoods' names as keys to access individual DataFrames with 'Group' and 'Value' columns.

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | Group | Name of the nationality group | String |
    | Value | Population value for the group in that neighborhood | Integer |


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

**GeoDataFrames**

- `prepare_gdf_rent(year)`: generates a GeoDataFrame with the rent per capita data for each neighborhood of Barcelona for a given year.

    ⮑ Input: year (int).

    ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'rent_per_capita'.

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | District | Name of the district | String |
    | Neighborhood | Name of the neighborhood | String |
    | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system | Geometry |
    | rent_per_capita | Rent per capita value for that neighborhood (in €)| Float |

- `prepare_gdf(lecture_function, add_spain, year)`: generates a GeoDataFrame with the Simpson's Diversity Index (SDI) for each neighborhood of Barcelona for a given year, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

    ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), year (int).

    ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'Simpsons_Diversity_Index'.

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | District | Name of the district  | String |
    | Neighborhood | Name of the neighborhood | String |
    | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system | Geometry |
    | Simpsons_Diversity_Index | Simpson's Diversity Index value for that neighborhood | Float [0,1) |

- `prepare_gdf_difference_df12(df1, df2)`: generates a GeoDataFrame with the percentage difference between two GeoDataFrames (df1 and df2) for each neighborhood of Barcelona.

    ⮑ Input: df1 (DataFrame), df2 (DataFrame).

    ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and ''Percentage_Difference'.

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | District | Name of the district  | String |
    | Neighborhood | Name of the neighborhood | String |
    | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system | Geometry |
    | Percentage_Difference | Percentage difference value between df1 and df2 for that neighborhood | Float |
- `df_difference(lecture_function, add_spain, initial_year, final_year)`: generates a GeoDataFrame with the percentage difference of the SDI between two years for each neighborhood of Barcelona, either including or excluding Spain as one of the nationalitys groups (depending on add_spain).

    ⮑ Input: lecture_function (dictionary format with neighborhoods as keys), add_spain (bool), initial_year (int), final_year (int).

    ⮑ Metadata: 'District', 'Neighborhood', 'Geometry_etrs89' and 'Diversity_difference'.

    | Field | Description | Type |
    | ----- | ----------- | ----- |
    | District | Name of the district  | String |
    | Neighborhood | Name of the neighborhood | String |
    | Geometry_etrs89 | Geometrical data in ETRS89 coordinate system | Geometry |
    | Diversity_difference | Percentage difference value of the SDI between the two years for that neighborhood | Float |


The explanation of the rest of the functions used for the analysis can be found in the README.md file located inside the folder directory `immigration-avdm/Alba`.


### Ale directory
There are two jupyter notebooks in this directory: 

- *0_reformat_data.ipynb*, which is required to run most of the codes in this repository and was explained in section **Uncode and reformat data**.
- *1_density_and_diversity.ipynb*, a code to generate several plots that give an overview of the immigration situation in Barcelona, which acts as a motivation for our project while giving rise to some initial results.


The latter can only be run after the first notebook since it works with datasets [1] and [2], which have coded values. It also requires an **additional Python library (Generativepy)** that cannot be installed through conda, so we used pip:

```console
conda activate ub-avbd
pip install generativepy
```

The code will **generate a folder *./Ale/img/* with the final plots** of this study:

1. **Density Comparison**: 2x2 axes containing (1997 and 2025) x (Total and Immigrant population densities) per neighborhood density colormaps with a single legend (colorbar) added as an extra axis, which has a logarithmic scale.
2. **Dominant Group x Share**: bivariate colormap that reveals the most present immigrant group on each neighborhood in 2025 and the share it represents among immigrants.
3. **Diversity Comparison**: 1x2 axes with colormaps of the total and immigrant diversities in 2025 resulting from the normalized Shannon Entropy indicator. The plot displays a single legend (colorbar) added as an extra axis.
4. **Diversity Interpretation**: horizontal bars for three relevant neighborhoods that display high, medium and low diversity in 2025 (on the resulting spectrum). They illustrate the relevance of different population groups for each normalized Shannon Entropy. This gives an idea on how to interpret this diversity index, which is not an intuitive quantity.


Although **not implemented** since we did not need to create files for this project, the treated **data** used for all plots **can be easily computed and exported to *.csv* files** (or any desired format) with two functions created.

- `data_density(year)`: generates one of the DataFrames used in figure (1), which has all the information for the specified year.

   | Field | Description | Type |
   | ----- | ----------- | ---- |
   | District  | District name | str |
   | Neighborhood | Neighborhood name | str |
   | Geometry_etrs89 | Geometry of the neighborhood in etrs89 format | geometry |
   | Population_Spain | Spanish population in the neighborhood | numeric |
   | Population_outside_Spain | Immigrant population in the neighborhood | numeric |
   | Total_Population | Spanish + Immigrant population in the neighborhood | numeric |
   | Immigrant_percentage | Percentage of immigrants with respect to the total population in the neighborhood | numeric |
   | Area_km2 | Area in square kilometers of the neighborhood | numeric |
   | Population_density | Total population in a neighborhood divided by its area | numeric |
   | Immigrant_density | Immigrant population in a neighborhood divided by its area | numeric |

- `data_diversity(year)`: generates the DataFrame used in figures (2), (3) and (4), which has all the information for the desired year.

   | Field | Description | Type |
   | ----- | ----------- | ---- |
   | District  | District name | str |
   | Neighborhood | Neighborhood name | str |
   | Geometry_etrs89 | Geometry of the neighborhood in etrs89 format | geometry
   | \<Group> | Immigration group's population in the neighborhood after rearranging original regions into a smaller set | numeric |
   | Spain | Spanish population in the neighborhood | numeric |
   | Total_Immigrants | Immigrant population in the neighborhood | numeric |
   | Total_Population | Spanish + Immigrant population in the neighborhood | numeric |
   | \<Group>_share | Population of the group divided by the immigrant population, both in the neighborhood | numeric |
   | \<Group>_total_share | Population of the group divided by the total population, both in the neighborhood | numeric |
   | Dominant_Group | Name of the biggest immigrant group in the neighborhood | str |
   | Dominant_Group_Value | Population of the biggest immigrant group in the neighborhood | numeric |
   | Dominant_Group_share | Population of the biggest immigrant group divided by the immigrant population, both in the neighborhood | numeric |
   | Dominant_Group_total_share | Population of the biggest immigrant group divided by the total population, both in the neighborhood | numeric |
   | Diversity | Shannon Entropy (diversity indicator) computed over the immigrant population groups in the neighborhood | numeric
   | Diversity_Norm | Shannon Entropy normalized by dividing over the logarithm of the number of immigrant groups considered | numeric |
   | Diversity_Total | Shannon Entropy (diversity indicator) computed over the total population in the neighborhood | numeric
   | Diversity_Total_Norm | Shannon Entropy normalized by dividing over the logarithm of the number of immigrant groups considered + 1 for the Spanish population | numeric |


Both functions return a DataFrame that can be exported as a *.csv*. Here is an **example** on how to use them:

    df = data_density(2025)
    df.to_csv('<directory>/<filename>.csv', index=False)

where <...> has to be substituted with the desired output.


### Pablo directory
This directory contains code for analyzing immigration patterns in Barcelona by geographical region and birthplace. The analysis focuses on three main aspects: overall immigration trends, gender distribution in Asian immigration, and spatial distribution of Southern Asian immigration.

There are six **notebooks** in this directory: 
- 0_merged_data.ipynb - Data Preparation. It merges yearly CSV files from two main datasets into consolidated files:
   + merged_birthPlaceRegion_sex.csv: Population by UN geographical region of birth and sex
   + merged_birthPlace_spain_v_outside.csv: Population by birthplace (Spain vs. outside Spain)
- 0_0_Percentage_immigration_neighborhood.ipynb - Immigration by neighborhood. It creates maps of Barcelona showing the immigration percentage per neighborhood through time from 1997-2025.
- 1_Total_immigration_temporal.ipynb - Overall Immigration Trends. It analyzes the evolution of Barcelona's population by origin (Spain-born vs. foreign-born) from 1997-2025.
- 1_Percentage_total_city_2025.ipynb - Regional Distribution. It creates a donut chart showing Barcelona's 2025 population distribution by region of birth, separating Spain-born from other Southern European populations.
- 2_Gender_distribution_Population.ipynb - Gender Analysis. It compares the gender distribution of immigrants from Southern Asia and Eastern Asia over time (1997-2025) with linear and logarithmic scales.
- 3_Heat_map_SouthAsia.ipynb - Spatial Distribution. It analyzes the distribution of Southern Asian immigrants across Barcelona's districts and neighborhoods, with comparisons to Latin American immigration patterns.

**Data Sets Used**:
There were two datasets used:
- Dataset 1: Population by geographical region of birth and sex (UN regions)
- Dataset 2: Population by birthplace and sex (Spain vs. outside Spain)

**Outputs**:
The code generates several visualizations stored in ../data/outputs/good/ (if this folder does not exist it is created):

- Population Evolution (1997-2025): Stacked area chart showing Spain-born vs. foreign-born population growth with percentage labels.
- Regional Distribution Donut Chart: Visual breakdown of Barcelona's 2025 population by region of birth.
- Gender Distribution Comparison: 2×2 panel plot comparing male/female immigration from Southern and Eastern Asia.
- Heatmap and Stacked Area Charts: District-level heatmap of Southern Asian population (linear and log scales) and Neighborhood-level stacked area chart for Ciutat Vella district
- Comparative heatmap: Southern Asia vs. Latin America immigration

**Generated Data Frames**:
neighborhood_population_summary.csv (1997-2025): Yearly population statistics by neighborhood.
| Field | Description | Type |
|-------|-------------|------|
| Year_Reference | Year (January 1st) | numeric |
| District | District name | str |
| Neighborhood | Neighborhood name | str |
| total_population | Total population | numeric |
| spain_population | Spain-born population | numeric |
| outside_spain | Foreign-born population | numeric |
| eu_population | EU-born population (excluding Spain) | numeric |
| world_population | Non-EU foreign-born population | numeric |
| pct_outside_spain | Percentage of foreign-born population | numeric |

### Sara directory
This directory contains all the codes used in the creation of the mini article "Assessing the Socioeconomic and Educational Effects of Immigration in Barcelona".  It consist of four .ipynb files: 0_data_process.ipynb does a first cleaning and process of the datasets that are going to be used (3,4 and 5) in the creation of the different figures, saving them in a folder (local) called "generated_data"; and the other three correspond to the generation of the figures themselves, that we are going to discuss next. Two other folders (local) are added to Sara directory: one with the name "outputs", to save the results of the plots; and other named "images", where the files legend1.png and legend2.png have to be saved for them to be used as a legend in the bubble chart. These can be found in the link to the repository's drive.

We used the following generated data frames in each plot:

1. **1_bubble_chart.ipynb: correlation between socioeconomic indices and education in the different neighborhoods of Barcelona**
   CSV file name: postcompulsory_percentages_1997-2025.csv
   | Field            | Description | Type |
   |------------------|-------------|------|
   |Year_Reference | Year at first of January | numeric |
   | District | District name |str |
   | Neighborhood  | Neighborhood name | str |
   | Total_Population  | Total population of the district | numeric |
   | Total_Postmandatory  | Population of the district with post-compulsory studies | numeric |
   | Postmandatory_Inmigrants  | Immigrants of the district with post-compulsory studies | numeric |
   | Total_Inmigrants  | Total immigrants of the district | numeric |
   | Percentage_Postmandatory  | Percentage of population of the district with post-compulsory studies | numeric |
   | Total_Postmandatory_Inmigrants  | Percentage of immigrants of the district with post-compulsory studies | numeric |

   CSV file name: indices_2015-2022.csv
   | Field (Original)  | English Term       | Description | Type |
   |-------------------|--------------------|-------------|------|
   | año           | Year             | Year at first of January |  numeric |
   | barrios de Barcelona    | Barcelona's neighborhoods  | Neighborhood name | str |
   | extranjeros de países de renta baja o media (%) | Foreigners from low- and middle-income countries (%) | Percentage in the neighborhood | numeric |
   | población ocupada (%) | Employed population (%) | Percentage in the neighborhood | numeric |
   | renta media por persona (€) | Average income per person (€) | Amount in the neighborhood | numeric |
   | trabajadores de baja calificación (%) | Low qualified workers (%) | Percentage in the neighborhood | numeric |

2. **2_heatmap_verticalbars.ipynb: correlation between the educational level of Barcelona's districts and the average income per person**
   CSV file name: education_percentages_1997-2025.csv
   | Field            | Description | Type |
   |------------------|-------------|------|
   |Year_Reference | Year at first of January | numeric |
   | District | District name | str |
   | Education_Level  | Different levels of education | str |
   | Value  | Number of people with a determined level of education in each district | numeric |
   | Total_District  | Total population of the district | numeric |
   | Percentage  | Percentage of population with a determined level of education in each district | numeric |

3. **3_horizontalbars.ipynb: Origin continent of high-studied population in Barcelona’s districts and correlation with the income**
   | Field (Original)  | English Term       | Description | Type |
   |-------------------|--------------------|-------------|------|
   | Territorio           | Region             | District name | str |
   | Titulación académica    | Academic title  | Different levels of education | str |
   | Poblacion | Population | Number of people with a determined level of education in each district | numeric |
   | Continente | Continent | Continent names | str |
   | group_continent | group_continent | Continent names with America and Oceania grouped | str |

### Sergi Directory
This directory contains a single .ipynb file which creates all the figures necessary for the "Is the immigration in Barcelona the cause of the Spain-born citizens’ emigration?" mini article. The csv files containing the data generated are stored in the data folder (local), in a created by the program folder called "sergi_data_frames". Apart from that, another folder called "figures_sergi" (local) is created inside the Sergi directory containing all the generated figures in .png and .pdf format. The data sets used are 1, 2 and 6.  

There are three types of plots generated (and its corresponding data frames):
1. **Scatter plot by world region to analyze the influence of the variation of the immigrant percentage in the total Spain-born population by neighborhood**  
   CSV file name: (world_region)_(district/neighborhood/city)_scatter.csv
   | Field            | Description | Type |
   |------------------|-------------|------|
   | Neighborhood  | Neighborhood name | str |
   | District | District name | str |
   |Year_Reference | Year (January 1st) (i) | numeric |
   |Pop_Spain_diff | Difference in the Spain-born population between year (i+period) and year (i) | numeric |
   |Perc_Outside_diff | Difference in the foreign-born (world_region) population percentage between year (i) and year (i-period) | numeric |

3. **Bar plot comparing the evolution of the difference between consecutive years of a certain immigrant group and the Spain-born population for a certain district, neighbourhood, or city.**  
   CSV file name: bars_(world_region)_(district/neighborhood/city).csv  
   | Field            | Description | Type |
   |------------------|-------------|------|
   | District/Neighborhood  | District or Neighborhood name (all rows the same). This column does not appear if the data frame corresponds to the whole city. | str |
   |Year_Reference |Year (January 1st) (i) | numeric |
   |D_ESP | Difference in the Spain-born population between year (i) and year (i-1) | numeric |
   |D_WR | Difference in the foreign-born (world_region) population between year (i) and year (i-1) | numeric |
4. **Double y-axis graphics comparing the variation of the Spain-born and the Latin America-born population between consecutive years for the city of Barcelona (left axis) with the time evolution of
the unemployment rate in the province of Barcelona (right axis)**  
   CSV file name (a): unemployment_rate_province_BCN.csv
   | Field (Original)  | English Term       | Description | Type |
   |-------------------|--------------------|-------------|------|
   | Periodo           | Period             | Time period (Year+Quarter) | str |
   | Tasa    | Rate  | Type of rate (in this case only unemployment)| str |
   |Total | Total | Unemployment rate (%) | numeric |
   |Year_decimal | Year_decimal | Year + (Quarter-1)/4)-0.5 | numeric |
   
   CSV file name (b): LATAM_BCN_difference.csv
   | Field            | Description | Type |
   |------------------|-------------|------|
   |Year_Reference | Year (January 1st) (i) | numeric |
   |D_ESP | Difference in the Spain-born population between year (i) and year (i-1) | numeric |
   |D_WR | Difference in the Latin american population between year (i) and year (i-1) | numeric |
