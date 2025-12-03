# immigration-avdm


## Contributors:

- Pablo Barquín Soria
- Sara González Basdediós
- Alba López Rivas
- Sergi Martínez Galindo
- Alejandro Palacios Garrido

## Data information

### Data sets

- **Population by geographical region of birth and sex**  
  <https://opendata-ajuntament.barcelona.cat/data/ca/dataset/pad_mdb_lloc-naix-regio_sexe>

  | Field            | Description                                                                                                                                          |
  |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Data_Referencia  | The reference date for the data point.                                                                                                               |
  | Codi_Districte   | Code of the district. More information at Administrative units of the city of Barcelona.                                                             |
  | Nom_Districte    | Name of the district.                                                                                                                                |
  | Codi_Barri       | Code of the neighborhood. More information at Administrative units of the city of Barcelona.                                                         |
  | Nom_Barri        | Name of the neighborhood.                                                                                                                            |
  | Valor            | Number of people (the count).                                                                                                                        |
  | LLOC_NAIX_REGIO  | Geographical region of birth. See descriptions in the Dimensions of the Municipal Register of Inhabitants datasets.                                  |
  | SEXE             | Sex. See descriptions in the Dimensions of the Municipal Register of Inhabitants datasets.                                                           |

- **Population by birthplace and sex**  
  <https://opendata-ajuntament.barcelona.cat/data/en/dataset/pad_mdbas_lloc-naix_sexe>

  | Field            | Description                                                                                                                                          |
  |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Data_Referencia  | Reference Date                                                                                                                                       |
  | Codi_Districte   | District Code. More information at Administrative units of the city of Barcelona.                                                                    |
  | Nom_Districte    | District Name                                                                                                                                        |
  | Codi_Barri       | Neighborhood Code. More information at Administrative units of the city of Barcelona.                                                                |
  | Nom_Barri        | Neighborhood Name                                                                                                                                    |
  | AEB              | Basic Statistical Area (Àrea estadística bàsica). More information at Administrative units of the city of Barcelona.                                 |
  | Seccio_Censal    | Census Section. More information at Administrative units of the city of Barcelona.                                                                   |
  | Valor            | Value (Number of people)                                                                                                                             |
  | LLOC_NAIX        | Place of Birth. See descriptions in Dimensions of the Municipal Register of Inhabitants datasets of the city of Barcelona.                           |
  | SEXE             | Sex. See descriptions in Dimensions of the Municipal Register of Inhabitants datasets of the city of Barcelona.                                     |

- **Population aged 16+ by level of education and birthplace**  
  <https://opendata-ajuntament.barcelona.cat/data/en/dataset/pad_mdb_niv-educa-esta_edat-lloc-naix>

  | Field            | Description                                                                                                                                          |
  |------------------|------------------------------------------------------------------------------------------------------------------------------------------------------|
  | Data_Referencia  | The reference date for the data point.                                                                                                               |
  | Codi_Districte   | Code of the district. More information at Administrative units of the city of Barcelona.                                                             |
  | Nom_Districte    | Name of the district.                                                                                                                                |
  | Codi_Barri       | Code of the neighborhood. More information at Administrative units of the city of Barcelona.                                                         |
  | Nom_Barri        | Name of the neighborhood.                                                                                                                            |
  | Valor            | Number of people (the count).                                                                                                                        |
  | NIV_EDUCA_esta   | Academic degree or qualification. See descriptions in the Dimensions of the Municipal Register of Inhabitants datasets of the city of Barcelona.     |
  | LLOC_NAIX        | Place of birth. See descriptions in the Dimensions of the Municipal Register of Inhabitants datasets of the city of Barcelona.                       |

- **Population aged 16+ by level of education and continent of birth**  
  <https://portaldades.ajuntament.barcelona.cat/es/estadísticas/r8qejecnob>

  | Field               | Description                                                                                           |
  |---------------------|-------------------------------------------------------------------------------------------------------|
  | Territorio          | Different neighborhoods of Barcelona.                                                                 |
  | Titulación académica| Possible academic degrees or qualifications.                                                          |
  | Continentes         | Continent of birth: Africa, América, Asia, Europa, Oceanía, Not Available.                            |
  | Año                 | The year (1997–2025).                                                                                 |

- **Socioeconomic indicators by neighborhood**  
  <https://www.idescat.cat/pub/?id=ist&n=14075&geo=mun:080193&lang=es>

  | Field                                   | Description                                                                                           |
  |-----------------------------------------|-------------------------------------------------------------------------------------------------------|
  | Neighborhood                            | Different neighborhoods of Barcelona.                                                                 |
  | Población ocupada (%)                   | Percentage of occupied population in the different neighborhoods.                                     |
  | Trabajadores de baja calificación (%)   | Percentage of low-qualified population in the different neighborhoods.                                |
  | Población con estudios bajos (%)        | Percentage of population with low studies in the different neighborhoods.                              |
  | Población joven sin estudios postobligatorios (%) | Percentage of young population without post-compulsory studies.                                       |
  | Extranjeros de países de renta baja o media (%) | Percentage of foreigners from low- and middle-income countries in the neighborhoods.                   |
  | Renta media por persona (€)             | Average income per person in the different neighborhoods.                                             |

- **Rates of activity, unemployment and employment by province and sex**  
  <https://datos.gob.es/en/catalogo/ea0010587-tasas-de-actividad-paro-y-empleo-por-provincia-y-sexo-epa-identificador-api-72989?utm_source=chatgpt.com>

  | Field (Original)  | English Term       | Description                                                                                                      |
  |-------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
  | Periodo           | Period             | The time period of the data (e.g., Quarter T1–T4, or Year).                                                      |
  | Provincia         | Province           | Name of the Spanish province (e.g., Barcelona, Madrid, Valencia).                                                |
  | Codigo Provincia  | Province Code      | The unique numerical code assigned to each province.                                                             |
  | Sexo              | Sex                | Sex of the population segment (Male, Female, Total).                                                             |
  | Tasa de Actividad | Activity Rate      | Percentage of working-age population that is employed or actively seeking employment.                            |
  | Tasa de Paro      | Unemployment Rate  | Percentage of the labor force that is unemployed and actively seeking work.                                      |
  | Tasa de Empleo    | Employment Rate    | Percentage of the working-age population that is currently employed.                                             |


### Data translation

### Where to store the data locally

### Data generation

## Code excution

### Alba directory

### Ale directory

### Pablo directory

### Sara directory

### Sergi Directory
This directory contains a single .ipynb file which creates all the figures necessary for the "Is the immigration in Barcelona the cause of the Spain-born citizens’ emigration?" mini article. The csv files containing the data generated are stored in the data folder (local), with a folder name "sergi_data_frames". Apart from that, another folder is created inside the Sergi directory called "figures_sergi" containing all the generated figures in .png and .pdf format, this folder will only appear locally.
