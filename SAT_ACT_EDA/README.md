# Does Poverty Rate Affect Student Performance in Standardized Tests?

Standardized tests are generally used in the United States as a requirement for university applications and admissions, with the ACT and SAT being the two most well-established and widely accepted tests for university admissions. Any student who is able to score above a certain benchmark is able to gain access to a wide range of universities, hence allowing them obtain better education in better schools. However, recent researches and articles have come out to classify these tests as biased against students who grew up in poorer living condtions, or in short, poverty.

### Problem Statement

The aim of the analysis will be focused on determining whether there is a correlation between poverty rate and ACT/SAT performances on the state-wide level, and if so, what are some recommendations and measures that the states of interest can implement to make taking the standardized tests more equitable or whether states should start abolishing standardized tests as a whole.

### Data Dictionary

To suppport the analysis, the most recent datasets for the standardized tests have been selected, along with the 2019 Poverty and Median Household Income Estimates on for each state, which was extracted from the US Census Bureau, Small Area Income and Poverty Estimates (SAIPE) Program.

|Feature|Type|Dataset|Description|
|---|---|---|---|
|composite|float|ACT_2019|The average composite score of each US state.| 
|total|integer|SAT_2019|The average total score of each US state. (EBRW + Math)|
|participation|float|ACT_2019, SAT_2019|The participation rate of the ACT in 2019 of each US state.|
|poverty_percent__age_5_17_in_families|float|PovertyRate_2019|The poverty percentage of children aged 5 to 17 within families in poverty of each US state.|

### Analysis

Based on the data analysis done for the above-mentioned datasets, the poverty rate was negatively correlated with the ACT and SAT scores in 2019. The mean poverty rate was at approximately 15%, ACT mean composite score was 21.5, and SAT mean total score was 1113. These means were used as baselines to determine the states which have higher numbers of families living in poverty, and their test performances. For all the states where taking the ACT and SAT is compulsory (participation rate = 100%) in 2019, all the scores for the two tests were seen to be lower than their respective mean scores. According to the heatmaps generated, it could be observed that there were negative correlations between the poverty rate and the scores of the ACT and SAT. However, the effect scores of the correlations were small, hence the relationship is not direct. 

On the other hand, there are some states that have high ACT and SAT scores, but have high poverty rates. This may be due to the fact that taking the tests in these states are optional, as reflected by the low participation rate, and the students that take part would have more accessibility to proper test preparation resources, and hence being wealthier than majority of the other students in the state, resulting in the discrepancy.

### Conclusion & Recommendations

To conclude the overall analysis, though not direct, there were slight negative correlations between the average scores of the ACT and SAT with the poverty rate of each US state. The outliers that were observed in the graphical analysis also proves that given the proper learning environment and resources, the students living in relatively more impoverished conditions can have more confidence in taking the standardized tests and also getting good scores on them.

As implementing measures for every state at once is difficult, changes can be started at states where taking standardized tests are compulsory but have relatively higher poverty rates. States like Alabama, Florida, Louisiana and Mississippi, can increase funding for less privileged students to attend test preparation classes, and for schools in poorer states to be able to provide better support for the students in taking the standardized tests. On the other hand, given the dropping popularity of the tests, colleges may also consider making these tests optional for college admission.

### References

- act2019_cleaned.csv
- sat2019_cleaned.csv
- US Census Bureau, Small Area Income and Poverty Estimates (SAIPE) Program, "SAIPE State and County Estimates for 2019", Dec 2020, https://www.census.gov/data/datasets/2019/demo/saipe/2019-state-and-county.html
