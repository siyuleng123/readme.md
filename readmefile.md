<h1 align="center">Welcome to The Project: Analysis on the Factors Affecting Self-Rated Health of the Elderly in China 👋👋</h1>


## Overview and Purpose

China's population is aging at an extremely rapid rate. It is expected that China's population aged 65 and above will increase from 119 million in 2010 to 360 million by 2050. The health problem of the elderly is a social issue worthy of attention. This study uses the China Health and Retirement Longitudinal Study (CHARLS) 2011-2012 baseline survey data, and uses multi-level generalized linear models to try to evaluate the factors that affect self-rated health from both the community and individual levels.



## Data Source

The CHARLS dataset can be obtained from the official website of the China Health and Retirement Longitudinal Study (CHARLS) at https://charls.pku.edu.cn/. The dataset is available for free and requires registration to access.

## Data Specification

The survey was conducted in 28 provinces, autonomous regions, and municipalities directly by Government (excluding Hong Kong, Macao, Taiwan, Tibet, Ningxia, and Hainan Island), and 450 village-level units out of 150 county-level units were selected for the survey. The survey targets were residents over 45 years old, and the number of surveyed households reached 12,057, with a total of 17,708 people. This survey is currently the only nationwide survey in my country that also targets middle-aged and elderly people. The questionnaire collected extensive information on individuals, families and communities, which better met the data needs of this study.

The dataset contains multiple waves of survey data collected over time, allowing for longitudinal analysis. It covers a wide range of variables, including but not limited to:

-	Demographic information (e.g., age, gender, education level)
-	Health-related information (e.g., chronic diseases, disabilities, healthcare utilization)
-	Cognitive function assessments
-	Economic indicators (e.g., income, employment status, retirement plans)
-	Social and family characteristics (e.g., marital status, living arrangements)
-	Geographic information (e.g., region, urban/rural classification)

| Questionnaire module        | Variable   |  Description  |
| :--------  | :-----  | :----:  |
B. Basic information| Demographic_Background Basic| demographics of the main respondents and their spouses information|
|C. Family information |Family_Information |Family and household member information|
|D. Health_Status_and_Functioning| Health_Status_and_Functioning |Health status, health behaviors, and cognitive abilities|
|F. Work and Retirement| Work_Retirement| Work and retirement status
|G1. Household income and expenditure| Household_Income| Household income, expenditure and housing situation|
|G2. Individual income| Individual_Income |Personal income|
|V. Epidemic| COVID_Module| Respondents’ relevant information during the epidemic|
|EX. Exit questionnaire| EXIT_Module, Weights, Sample_Infor | Information about deceased respondents, cross-sectional weights, sample information


The dataset is organized in a structured format, typically provided in commonly used data file formats such as CSV or Excel.

## Metadata Standard

The CHARLS dataset adheres to the Data Documentation Initiative (DDI) metadata standard. DDI provides a comprehensive framework for describing and documenting survey data, including information on study design, data collection methods, variable definitions, and data organization. The use of DDI ensures standardized and interoperable documentation of the CHARLS dataset.

## Data preparation

This study uses the individual and community levels as the basic framework to re-evaluate the influencing factors of the elderly's self-rated health. 

At the individual level, demographic variables, socioeconomic variables, lifestyle variables, health and medical-related variables are selected for analysis according to the general processing method; 

At the second level, the community level, it is planned to select community development level, community environment, community population and labor force Analyze other factors.

- Dependent variable:

  Self-rated health, the dependent variable is formed from the question "How do you feel about your health?" in the questionnaire. In studies of self-rated health we have found that different answer formats influence how respondents respond. Therefore, in the CHARLS questionnaire, this question is set into two different answers, and the respondents are randomly assigned to answer in one of the groups. The answer options for the first group are: excellent, very good, good, average, and bad. The answer options for the second group are: very good, good, average, bad, and very bad. Afterwards, the two sets of answers were combined into "Excellent", "Very Good" and "Good", and those with "Average", "Bad" and "Very Bad" were combined into "Poor" , assigned values of 1 and 0 respectively.

- Independent variables:

  The first is demographic factors, including gender, age, place of residence, marital status and education level. Gender, female and male are assigned values of 0 and 1 respectively. Age, select respondents who are 60 years or older. In the CHARLS data, marital status is divided into 6 different statuses such as "married and living with spouse" and "never married". This study simplifies them into "with spouse" and "other" and assigns a value of 1 respectively. ,0. In the CHARLS data, there are 11 levels of educational attainment ranging from “illiteracy” to “PhD graduate”. This study simplifies it into two groups: “primary school and below” and “above primary school”, which are assigned values of 0 and 1 respectively.
  
  The second is socioeconomic factors, including living standards and child support. Based on the respondents' answers about the average living standard compared with their neighbors, the living standard is divided into three categories: "worse than", "quite" and "better than", which are coded as dummy variables; while child support is divided into "no". " and "have" categories are assigned values of 0 and 1 respectively.
  
  The third is health and medical factors, including perceptions of emotional and mental illness, physical disabilities, and whether you have been to the hospital in the past month. This study uses the 11th item of the questionnaire about chronic diseases, that is, "do you suffer from emotional and mental diseases", and takes "do you know you have this disease" as the variable. Regarding physical disability, this study assigned a value of 1 for those with physical disability and a value of 0 for those without physical disability. Whether you have been to the hospital in the past month, the value of 0 is assigned if you have been to the hospital, and the value is 1 if you have not been.
  
  The fourth is lifestyle factors, including self-care ability, smoking, drinking, etc. Among them, the measurement of independent living ability (ADL) includes 6 items such as dressing, bathing, eating, getting in and out of bed, going to the toilet, and controlling urination and defecation. A value of 0 is assigned if the respondent has difficulty completing at least one ADL subitem on his or her own; a value of 1 is assigned if the respondent has no problem completing all 6 items. In this study, non-smoking was assigned a value of 0, and smoking was assigned a value of 1. Regarding drinking, there is a question in the questionnaire about whether you drank alcohol every month in the past year. This study assigned a value of 0 to those who did not drink and a value of 1 to those who drank.
  
  Community environment, measured using waste disposal methods and toilet types. Whether domestic waste is processed uniformly, the value of unified processing is assigned to 1, and the value of non-uniformized processing is assigned to 0. Regarding toilet types in the community, for the sake of simplicity, this study combined the five toilet types in the questionnaire into two categories: open toilets and non-open toilets, assigned values of 0 and 1 respectively.

## Methods

The dependent variable of this study was simplified into a dichotomous variable, involving both individual and community levels, so this study adopted a two-level logistic regression model. 

- First, the necessity of using a multi-level model was tested through an unconditional model that did not include any research independent variables; 
- Then, the above types of independent variables (demographic variables, socioeconomic variables, health care variables, lifestyle variables) were substituted into Ordinary logistic regression and community - individual two-level logistic regression, comparison
- Changes in the effect of independent variables to further explore the differences between models
- Finally, the community-level variables (garbage disposal methods, toilet types, proportion of illiterates, proportion of the population over 65 years old, and the proportion of migrant workers and business people) were put into the multi-level model in turn, and the random coefficient model was used to explore the characteristics of the community-level natural environment. The interaction between variables and individual-level independent variables, and the results obtained are analyzed and explained.

## Sharing

There is a more complex mechanism behind self-rated health. We can think of self-rated health as consisting of two parts: latent health and self-reporting behavior. Each influencing factor not only affects self-rated health by affecting latent health, but also shapes personal health concepts. , social expectations, tolerance and various psychological factors affect self-evaluation behavior, and thus affect self-evaluation of health; at the same time, potential health conditions will also affect the process of personal self-evaluation behavior. Therefore, more analytical perspectives are needed to study the generation mechanism and influencing factors of self-rated health itself.

## 🤝 Data Citation

Yaohui Zhao;John Strauss;Gonghuan Yang;John Giles;Peifeng (Perry) Hu; Yisong Hu;Xiaoyan Lei;Albert Park;James P. Smith;Yafeng Wang (2013). China Health and Retirement Longitudinal Study, 2011-2012 National Baseline Users’ Guide, National School of Development, Peking University.



## 📝 License

The specific terms and conditions of data usage, distribution, and licensing for the CHARLS dataset are determined by the China Health and Retirement Longitudinal Study (CHARLS) organization. Users should refer to the official CHARLS website or documentation for detailed information on the dataset's license and usage restrictions.

## Notes

My Open Researcher and Contributor ID is 
>https://orcid.org/0009-0008-2641-5139

This data uses the Data Documentation Initiative (DDI) metadata standard. DDI is an open source, free and widely used standard. I didn't look for template. I think the README should be concise and concise, so I wrote this document myself. I use an online markdown editor. This eliminates the need to download software and is very convenient to use. And it can display the effect of markdown in real time, which is of great help to me. I think the hardest part is figuring out what research direction I want to take and finding a suitable, reliable and universal data source.





