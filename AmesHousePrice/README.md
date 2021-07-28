# Project 2 - Ames Housing Data and Kaggle Challenge


## Problem Statement

The sales price of any specific house are based upon many types of features and characteristics that the house has. As such, this task is to make use of a dataset of housing sales in Ames, Iowa and tranform it into a predictive model that would help homeowners accurately judge the value of their houses for future and determine the points of improvement to increase the price.

## Data Import, Cleaning, EDA

To support the analysis, a training Ames Housing Dataset of 82 different variables was imported and cleaned. This involved the removal of unneccesssary variables, dealing with missing values by either imputing them with relevant data, or classifying them as 0 or 'None', which indicates the absence of the variables. One-hot encoding was applied to categorical variables to create dummy variables and convert them into numerical values, which would in the fitting of the various predictive models.

Once the data was transformed, some features were identified to exhibit strong correlations with the SalesPrice, with the higher correlation with SalesPrice being the Overall Quality (OverallQual) and Above Ground Living Area (Gr_Liv_Area). These feature generally consists of numeric value that ranges on a scale of low score of 1 (Very Poor) to 10 (Excellent), and continuous, numerical values, respectively. Some outliers were also identified through plotting the SalesPrice against the Overall Quality and Living Area, in which all will be dropped before the dataset is fitted against the models.

### Data Dictionary
|Attribute|Variable Type |Dataset|Description|
|---|---|---|---|
|**Id**|*Discrete*|Ames Housing|Unique ID for each property|
|**PID**|*Nominal*|Ames Housing|Parcel identification number - can be used with city web site for parcel review|
|**MS SubClass**|*Nominal*|Ames Housing|Identifies the type of dwelling involved in the sale|
|**MS Zoning**|*Nominal*|Ames Housing|Identifies the general zoning classification of the sale|
|**Lot Frontage**|*Continuous*|Ames Housing|Linear feet of street connected to property|
|**Lot Area**|*Continuous*|Ames Housing|Lot size in square feet|
|**Street**|*Nominal*|Ames Housing|Type of road access to property|
|**Alley**|*Nominal*|Ames Housing|Type of alley access to property|
|**Lot Shape**|*Ordinal*|Ames Housing|General shape of property|
|**Land Contour**|*Nominal*|Ames Housing|Flatness of the property|
|**Utilities**|*Ordinal*|Ames Housing|Type of utilities available|
|**Lot Config**|*Nominal*|Ames Housing|Lot configuration|
|**Land Slope**|*Ordinal*|Ames Housing|Slope of property|
|**Neighborhood**|*Nominal*|Ames Housing|Physical locations within Ames city limits (map available)|
|**Condition 1**|*Nominal*|Ames Housing|Proximity to various conditions|
|**Condition 2**|*Nominal*|Ames Housing|Proximity to various conditions (if more than one is present)|
|**Bldg Type**|*Nominal*|Ames Housing|Type of dwelling|
|**House Style**|*Nominal*|Ames Housing|Style of dwelling|
|**Overall Qual**|*Ordinal*|Ames Housing|Rates the overall material and finish of the house|
|**Overall Cond**|*Ordinal*|Ames Housing|Rates the overall condition of the house|
|**Year Built**|*Discrete*|Ames Housing|Original construction date|
|**Year Remod/Add**|*Discrete*|Ames Housing|Remodel date (same as construction date if no remodeling or additions)|
|**Roof Style**|*Nominal*|Ames Housing|Type of roof|
|**Roof Matl**|*Nominal*|Ames Housing|Roof material|
|**Exterior 1st**|*Nominal*|Ames Housing|Exterior covering on house|
|**Exterior 2nd**|*Nominal*|Ames Housing|Exterior covering on house (if more than one material)|
|**Mas Vnr Type**|*Nominal*|Ames Housing|Masonry veneer type|
|**Mas Vnr Area**|*Continuous*|Ames Housing|Masonry veneer area in square feet|
|**Exter Qual**|*Ordinal*|Ames Housing|Evaluates the quality of the material on the exterior |
|**Exter Cond**|*Ordinal*|Ames Housing|Evaluates the present condition of the material on the exterior|
|**Foundation**|*Nominal*|Ames Housing|Type of foundation|
|**Bsmt Qual**|*Ordinal*|Ames Housing|Evaluates the height of the basement|
|**Bsmt Cond**|*Ordinal*|Ames Housing|Evaluates the general condition of the basement|
|**Bsmt Exposure**|*Ordinal*|Ames Housing|Refers to walkout or garden level walls|
|**BsmtFin Type 1**|*Ordinal*|Ames Housing|Rating of basement finished area|
|**BsmtFin SF 1**|*Continuous*|Ames Housing|Type 1 finished square feet|
|**BsmtFin Type 2**|*Ordinal*|Ames Housing|Rating of basement finished area (if multiple types)|
|**BsmtFin SF 2**|*Continuous*|Ames Housing|Type 2 finished square feet|
|**Bsmt Unf SF**|*Continuous*|Ames Housing|Unfinished square feet of basement area|
|**Total Bsmt SF**|*Continuous*|Ames Housing|Total square feet of basement area|
|**Heating**|*Nominal*|Ames Housing|Type of heating|
|**Heating QC**|*Ordinal*|Ames Housing|Heating quality and condition|
|**Central Air**|*Nominal*|Ames Housing|Central air conditioning|
|**Electrical**|*Ordinal*|Ames Housing|Electrical system|
|**1st Flr SF**|*Continuous*|Ames Housing|First Floor square feet|
|**2nd Flr SF**|*Continuous*|Ames Housing|Second floor square feet|
|**Low Qual Fin SF**|*Continuous*|Ames Housing|Low quality finished square feet (all floors)|
|**Gr Liv Area**|*Continuous*|Ames Housing|Above grade (ground) living area square feet|
|**Bsmt Full Bath**|*Discrete*|Ames Housing|Basement full bathrooms|
|**Bsmt Half Bath**|*Discrete*|Ames Housing|Basement half bathrooms|
|**Full Bath**|*Discrete*|Ames Housing|Full bathrooms above grade|
|**Half Bath**|*Discrete*|Ames Housing|Half baths above grade|
|**Bedroom AbvGr**|*Discrete*|Ames Housing|Bedrooms above grade (does NOT include basement bedrooms)|
|**Kitchen AbvGr**|*Discrete*|Ames Housing|Kitchens above grade|
|**Kitchen Qual**|*Ordinal*|Ames Housing|Kitchen quality|
|**TotRms AbvGrd**|*Discrete*|Ames Housing|Total rooms above grade (does not include bathrooms)|
|**Functional**|*Ordinal*|Ames Housing|Home functionality (Assume typical unless deductions are warranted)|
|**Fireplaces**|*Discrete*|Ames Housing|Number of fireplaces|
|**Fireplace Qu**|*Ordinal*|Ames Housing|Number of fireplaces|
|**Garage Type**|*Nominal*|Ames Housing|Garage location|
|**Garage Yr Blt**|*Discrete*|Ames Housing|Year garage was built|
|**Garage Finish**|*Ordinal*|Ames Housing|Interior finish of the garage|
|**Garage Cars**|*Discrete*|Ames Housing|Size of garage in car capacity|
|**Garage Area**|*Continuous*|Ames Housing|Size of garage in square feet|
|**Garage Qual**|*Ordinal*|Ames Housing|Garage quality|
|**Garage Cond**|*Ordinal*|Ames Housing|Garage condition|
|**Paved Drive**|*Ordinal*|Ames Housing|Paved driveway|
|**Wood Deck SF**|*Continuous*|Ames Housing|Wood deck area in square feet|
|**Open Porch SF**|*Continuous*|Ames Housing|Open porch area in square feet|
|**Enclosed Porch**|*Continuous*|Ames Housing|Enclosed porch area in square feet|
|**3Ssn Porch**|*Continuous*|Ames Housing|Three season porch area in square feet|
|**Screen Porch**|*Continuous*|Ames Housing|Screen porch area in square feet|
|**Pool Area**|*Continuous*|Ames Housing|Pool area in square feet|
|**Pool QC**|*Ordinal*|Ames Housing|Pool quality|
|**Fence**|*Ordinal*|Ames Housing|Fence quality|
|**Misc Feature**|*Nominal*|Ames Housing|Miscellaneous feature not covered in other categories|
|**Misc Val**|*Continuous*|Ames Housing|Dollar-Value of miscellaneous feature|
|**Mo Sold**|*Discrete*|Ames Housing|Month Sold (MM)|
|**Yr Sold**|*Discrete*|Ames Housing|Year Sold (YYYY)|
|**Sale Type**|*Nominal*|Ames Housing|Type of sale|
|**SalePrice**|*Continuous*|Ames Housing|Sale price $$ (target)|

## Analysis

The dataset was fitted using the Linear, Ridge, and LASSO Regressions models to determine which model has the best R<sup>2</sup> score. According to the training model done and cross validation scores, the Linear and Ridge Regressions produced training sets that were overfitted while the LASSO Regression had a model with a good fit. Therefore, the LASSO model would be used for predicting the sale prices of other houses.

## Conclusions & Recommendations

Based on the modelling and looking at the regression coefficients, it can be observed that the features that the homeowners can  look to do to improve the value of their houses would be the Masonry Veneer Area and Basement Area, which have relatively positive coefficients. Aspiring homeowners or real estate investors can also look for houses in the Northridge Heights or Stone Brook neighbourhoods more houses that have a better chance of increasing in value. 