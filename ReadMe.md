# US Craft Beer Case Study

The purpose of this to provide an Exploratory Data Analysis and 
provide useful insights to Budweizer by investigating US craft beers, their characteristics, breweries and locatins they come from.

## github link
[DDS-CaseStudy1](https://github.com/malcolmccarlson/DDS-CaseStudy1)
The github directory is flat with the exception of the knitr markdown directory to hold markdown artifacts.  The repo holds files having to do with the project including the PowerPoint slide deck.


## Libraries Used
library(magrittr)
library(mice)
library(usmap)
library(ggplot2)
library(stringr)
library(data.table)
library(webdriver)
library(class)
library(caret)
library(e1071)

# Key data sets
The following code books for the two main data sets(nona,allbrews) was generated by dataMaid.  The dataset is nona, the combined, cleand and imputed data set from merging Breweries.csv and Beers.csv.  The second data set code book is for allbrews which is a subset of nona but with grouped styleClass data that reduces the styles used in the KNN.  Allbrews also merges the population data set from usmap library to support the maps in the project.

## -------------------------------------------------------------
##                 nona - Dataset after imputation
## -------------------------------------------------------------

Number of observations	2410
Number of variables	10

Codebook summary table

Label       |Variable Class|# unique values|Missing|Description
------------|--------------|---------------|-------|------------
Brewery_id  |integer       |558            |0.00 % |      	 
Brewery_name|factor        |551	           |0.00 % |       	  
City        |factor	       |384	           |0.00 % |
State       |character	   |51	           |0.00 % |
Beer_name   |factor	       |2305	         |0.00 % |
Beer_ID     |integer	     |2410         	 |0.00 % |	
ABV         |numeric	     |74	           |0.00 % |	
IBU         |integer    	 |107	           |0.00 % |
Style       |factor        |100	           |0.00 % |	
Ounces      |numeric	     |7	             |0.00 % |	


## Number of unique values	51
Observed factor levels: "AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC", "DE", "FL", "GA", "HI", "IA", "ID", "IL", "IN", "KS", "KY", "LA", "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NC", "ND", "NE", "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI", "SC", "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY".


## --------------------------------------------------------------
##                    allbrews Code book
## --------------------------------------------------------------
Data report overview
The dataset examined has the following dimensions:
Feature	Result
Number of observations	2410
Number of variables	18
Codebook summary table

Label        |Variable Class|# unique values|Missing|Description
-------------|--------------|---------------|-------|-----------
State        |character	    |51	            |0.00 % |	
Brewery_count|integer	      |25	            |0.00 % |	
count        |integer 	    |37	            |0.00 % |	
fips         |character	    |51	            |0.00 %	|
full         |character	    |51	            |0.00 %	|
pop_2015     |numeric	      |51	            |0.00 %	|
per_cap      |numeric	      |51	            |0.00 %	|
Brewery_id   |integer	      |558	          |0.00 %	|
Brewery_name |factor	      |551	          |0.00 %	|
City         |factor	      |384	          |0.00 %	|
Beer_name    |character	    |2305	          |0.00 %	|
Beer_ID      |integer	      |2410	          |0.00 %	|
ABV          |numeric	      |74	            |0.00 %	|
IBU          |integer	      |107	          |0.00 %	|
Style        |factor	      |100	          |0.00 %	|
Ounces       |numeric	      |7	            |0.00 %	|
class        |character	    |16	            |0.00 %	|
used         |logical	      |2	            |0.00 %	|

Variable list
State
Feature	Result
Variable type	character
Number of missing obs.	0 (0 %)
Number of unique values	51

Observed factor levels: "AK", "AL", "AR", "AZ", "CA", "CO", "CT", "DC", "DE", "FL", "GA", "HI", "IA", "ID", "IL", "IN", "KS", "KY", "LA", "MA", "MD", "ME", "MI", "MN", "MO", "MS", "MT", "NC", "ND", "NE", "NH", "NJ", "NM", "NV", "NY", "OH", "OK", "OR", "PA", "RI", "SC", "SD", "TN", "TX", "UT", "VA", "VT", "WA", "WI", "WV", "WY".


full
Feature	Result
Variable type	character
Number of missing obs.	0 (0 %)
Number of unique values	51
Mode	“Colorado”

Observed factor levels: "Alabama", "Alaska", "Arizona", "Arkansas", "California", "Colorado", "Connecticut", "Delaware", "District of Columbia", "Florida", "Georgia", "Hawaii", "Idaho", "Illinois", "Indiana", "Iowa", "Kansas", "Kentucky", "Louisiana", "Maine", "Maryland", "Massachusetts", "Michigan", "Minnesota", "Mississippi", "Missouri", "Montana", "Nebraska", "Nevada", "New Hampshire", "New Jersey", "New Mexico", "New York", "North Carolina", "North Dakota", "Ohio", "Oklahoma", "Oregon", "Pennsylvania", "Rhode Island", "South Carolina", "South Dakota", "Tennessee", "Texas", "Utah", "Vermont", "Virginia", "Washington", "West Virginia", "Wisconsin", "Wyoming".


class
Feature	Result
Variable type	character
Number of missing obs.	0 (0 %)
Number of unique values	16
Mode	“IPA”

Observed factor levels: "ale", "APA", "Blonde ale", "brown ale", "cider", "fruit", "hefeweizen", "IPA", "Kölsch", "lager", "other", "pilsner", "porter", "red ale", "stout", "witbier".

