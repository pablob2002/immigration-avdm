# immigration-avdm

## Contributors:

- Pablo Barquín Soria
- Sara González Basdediós
- Alba López Rivas
- Sergi Martínez Galindo
- Alejandro Palacios Garrido

## Introduction

## Data information

### Data sets

1. **Population by geographical region of birth and sex**  
   <https://opendata-ajuntament.barcelona.cat/data/ca/dataset/pad_mdb_lloc-naix-regio_sexe>

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

### Data translation

### Where to store the data locally

## Code excution

### Alba directory

### Ale directory

### Pablo directory

### Sara directory

### Sergi Directory
This directory contains a single .ipynb file which creates all the figures necessary for the "Is the immigration in Barcelona the cause of the Spain-born citizens’ emigration?" mini article. The csv files containing the data generated are stored in the data folder (local), with a folder name "sergi_data_frames". Apart from that, another folder (local) is created inside the Sergi directory called "figures_sergi" containing all the generated figures in .png and .pdf format. The data sets used are 1, 2 and 6.  

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
