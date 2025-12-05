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

- Pablo Barquín Soria
- Sara González Basdediós
- Alba López Rivas
- Sergi Martínez Galindo
- Alejandro Palacios Garrido

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

8. **Geometry**
   <>



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

### Alba directory

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

    | Field | Description |
    | ----- | ----------- |
    | District  | District name |
    | Neighborhood | Neighborhood name |
    | Geometry_etrs89 | Geometry of the neighborhood in etrs89 format |
    | Population_Spain | Spanish population in the neighborhood |
    | Population_outside_Spain | Immigrant population in the neighborhood |
    | Total_Population | Spanish + Immigrant population in the neighborhood |
    | Immigrant_percentage | Percentage of immigrants with respect to the total population in the neighborhood |
    | Area_km2 | Area in square kilometers of the neighborhood |
    | Population_density | Total population in a neighborhood divided by its area |
    | Immigrant_density | Immigrant population in a neighborhood divided by its area |

- `data_diversity(year)`: generates the DataFrame used in figures (2), (3) and (4), which has all the information for the desired year.

    | Field | Description |
    | ----- | ----------- |
    | District  | District name |
    | Neighborhood | Neighborhood name |
    | <Group> | Immigration group's population in the neighborhood after rearranging original regions into a smaller set |
    | Spain | Spanish population in the neighborhood |
    | Total_Immigrants | Immigrant population in the neighborhood |
    | Total_Population | Spanish + Immigrant population in the neighborhood |
    | \<Group>_share | Population of the group divided by the immigrant population, both in the neighborhood |
    | \<Group>_total_share | Population of the group divided by the total population, both in the neighborhood |
    | Dominant_Group | Name of the biggest immigrant group in the neighborhood |
    | Dominant_Group_Value | Population of the biggest immigrant group in the neighborhood |
    | Dominant_Group_share | Population of the biggest immigrant group divided by the immigrant population, both in the neighborhood |
    | Dominant_Group_total_share | Population of the biggest immigrant group divided by the total population, both in the neighborhood |
    | Diversity | Shannon Entropy (diversity indicator) computed over the immigrant population groups in the neighborhood |
    | Diversity_Norm | Shannon Entropy normalized by dividing over the logarithm of the number of immigrant groups considered |
    | Diversity_Total | Shannon Entropy (diversity indicator) computed over the total population in the neighborhood |
    | Diversity_Total_Norm | Shannon Entropy normalized by dividing over the logarithm of the number of immigrant groups considered + 1 for the Spanish population |


Both functions return a DataFrame that can be exported as a *.csv*. Here is an **example** on how to use them:

    df = data_density(2025)
    df.to_csv('<directory>/<filename>.csv', index=False)

where <...> has to be substituted with the desired output.


### Pablo directory
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
| Field | Description |
|-------|-------------|
| Year_Reference | Year (January 1st) |
| District | District name |
| Neighborhood | Neighborhood name |
| total_population | Total population |
| spain_population | Spain-born population |
| outside_spain | Foreign-born population |
| eu_population | EU-born population (excluding Spain) |
| world_population | Non-EU foreign-born population |
| pct_outside_spain | Percentage of foreign-born population |

### Sara directory
This directory contains all the codes used in the creation of the mini article "Assessing the Socioeconomic and Educational Effects of Immigration in Barcelona".  It consist of four .ipynb files: 0_data_process.ipynb does a first cleaning and process of the datasets that are going to be used (3,4 and 5) in the creation of the different figures, saving them in a folder (local) called "generated_data"; and the other three correspond to the generation of the figures themselves, that we are going to discuss next. Two other folders (local) are added to Sara directory: one with the name "outputs", to save the results of the plots; and other named "images", where the files legend1.png and legend2.png have to be saved for them to be used as a legend in the bubble chart. These can be found in the link to the repository's drive.

We used the following generated data frames in each plot:

1. **1_bubble_chart.ipynb: correlation between socioeconomic indices and education in the different neighborhoods of Barcelona**
   CSV file name: postcompulsory_percentages_1997-2025.csv
   | Field            | Description |
   |------------------|-------------|
   |Year_Reference | Year at first of January |
   | District | District name |
   | Neighborhood  | Neighborhood name |
   | Total_Population  | Total population of the district |
   | Total_Postmandatory  | Population of the district with post-compulsory studies |
   | Postmandatory_Inmigrants  | Immigrants of the district with post-compulsory studies |
   | Total_Inmigrants  | Total immigrants of the district |
   | Percentage_Postmandatory  | Percentage of population of the district with post-compulsory studies |
   | Total_Postmandatory_Inmigrants  | Percentage of immigrants of the district with post-compulsory studies |

   CSV file name: indices_2015-2022.csv
   | Field (Original)  | English Term       | Description |
   |-------------------|--------------------|-------------|
   | año           | Year             | Year at first of January |
   | barrios de Barcelona    | Barcelona's neighborhoods  | Neighborhood name |
   | extranjeros de países de renta baja o media (%) | Foreigners from low- and middle-income countries (%) | Percentage in the neighborhood |
   | población ocupada (%) | Employed population (%) | Percentage in the neighborhood |
   | renta media por persona (€) | Average income per person (€) | Amount in the neighborhood |
   | trabajadores de baja calificación (%) | Low qualified workers (%) | Percentage in the neighborhood |

2. **2_heatmap_verticalbars.ipynb: correlation between the educational level of Barcelona's districts and the average income per person**
   CSV file name: education_percentages_1997-2025.csv
   | Field            | Description |
   |------------------|-------------|
   |Year_Reference | Year at first of January |
   | District | District name |
   | Education_Level  | Different levels of education |
   | Value  | Number of people with a determined level of education in each district |
   | Total_District  | Total population of the district |
   | Percentage  | Percentage of population with a determined level of education in each district |

3. **3_horizontalbars.ipynb: Origin continent of high-studied population in Barcelona’s districts and correlation with the income**
   | Field (Original)  | English Term       | Description |
   |-------------------|--------------------|-------------|
   | Territorio           | Region             | District name |
   | Titulación académica    | Academic title  | Different levels of education |
   | Poblacion | Population | Number of people with a determined level of education in each district |
   | Continente | Continent | Continent names |
   | group_continent | group_continent | Continent names with America and Oceania grouped |

### Sergi Directory
This directory contains a single .ipynb file which creates all the figures necessary for the "Is the immigration in Barcelona the cause of the Spain-born citizens’ emigration?" mini article. The csv files containing the data generated are stored in the data folder (local), in a created by the program folder called "sergi_data_frames". Apart from that, another folder called "figures_sergi" (local) is created inside the Sergi directory containing all the generated figures in .png and .pdf format. The data sets used are 1, 2 and 6.  

There are three types of plots generated (and its corresponding data frames):
1. **Scatter plot by world region to analyze the influence of the variation of the immigrant percentage in the total Spain-born population by neighborhood**  
   CSV file name: (world_region)_(district/neighborhood/city)_scatter.csv
   | Field            | Description |
   |------------------|-------------|
   | Neighborhood  | Neighborhood name |
   | District | District name |
   |Year_Reference | Year (i) |
   |Pop_Spain_diff | Difference in the Spain-born population between year (i+period) and year (i) |
   |Perc_Outside_diff | Difference in the foreign-born (world_region) population percentage between year (i) and year (i-period) |

3. **Bar plot comparing the evolution of the difference between consecutive years of a certain immigrant group and the Spain-born population for a certain district, neighbourhood, or city.**  
   CSV file name: bars_(world_region)_(district/neighborhood/city).csv  
   | Field            | Description |
   |------------------|-------------|
   | District/Neighborhood  | District or Neighborhood name (all rows the same). This column does not appear if the data frame corresponds to the whole city. |
   |Year_Reference | Year (i) |
   |D_ESP | Difference in the Spain-born population between year (i) and year (i-1) |
   |D_WR | Difference in the foreign-born (world_region) population between year (i) and year (i-1) |
4. **Double y-axis graphics comparing the variation of the Spain-born and the Latin America-born population between consecutive years for the city of Barcelona (left axis) with the time evolution of
the unemployment rate in the province of Barcelona (right axis)**  
   CSV file name (a): unemployment_rate_province_BCN.csv
   | Field (Original)  | English Term       | Description |
   |-------------------|--------------------|-------------|
   | Periodo           | Period             | Time period (Year+Quarter) |
   | Tasa    | Rate  | Type of rate (in this case only unemployment)|
   |Total | Total | Unemployment rate (%) |
   |Year_decimal | Year_decimal | Year + (Quarter-1)/4)-0.5 |
   
   CSV file name (b): LATAM_BCN_difference.csv
   | Field            | Description |
   |------------------|-------------|
   |Year_Reference | Year (i) |
   |D_ESP | Difference in the Spain-born population between year (i) and year (i-1) |
   |D_WR | Difference in the Latin american population between year (i) and year (i-1) | 
