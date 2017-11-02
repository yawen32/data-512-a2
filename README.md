# data-512-a2: Bias in data

## Goal
The goal of this project is to explore the concept of bias by analyzing the data of policical articles from different countries on Wikepidia. The project is supposed to perform an analysis from two aspects: existence and quality of policial articles for each country. The project should be fully reproducible by others by reading all resources listed in README file and following the step by step instructions in `hcds-a2-bias.ipynb`.


## Data
**There are two datasets need to be used in this project, read through all documentations and introductions carefully before you can download and use them. These datasets are also included in the repository.** 

1. Wikipedia article dataset

This dataset contains data on most English-language Wikipedia articles within the category "Category:Politicians by nationality" and subcategories. 

Columns are:

 - country: sanitised country name, extracted from the category name

 - page: unsanitised page title

 - last_edit: edit ID of the last edit to the page


Documentation can be found on [figshare website](https://figshare.com/articles/Untitled_Item/5513449)

Download [here](https://ndownloader.figshare.com/files/9614893)

**Note:** Unzip the file downloaded from the above link, the required dataset locates in \country\data named page_data.csv.

2. Population dataset

This dataset contains the populations of a variety of countries.

Check the data on [Population Research Bureau website](http://www.prb.org/DataFinder/Topic/Rankings.aspx?ind=14)

Download [here](http://www.prb.org/RawData.axd?ind=14&fmt=14&tf=76&loc=34235%2c249%2c250%2c251%2c252%2c253%2c254%2c34227%2c255%2c257%2c258%2c259%2c260%2c261%2c262%2c263%2c264%2c265%2c266%2c267%2c268%2c269%2c270%2c271%2c272%2c274%2c275%2c276%2c277%2c278%2c279%2c280%2c281%2c282%2c283%2c284%2c285%2c286%2c287%2c288%2c289%2c290%2c291%2c292%2c294%2c295%2c296%2c297%2c298%2c299%2c300%2c301%2c302%2c304%2c305%2c306%2c307%2c308%2c311%2c312%2c315%2c316%2c317%2c318%2c319%2c320%2c321%2c322%2c324%2c325%2c326%2c327%2c328%2c34234%2c329%2c330%2c331%2c332%2c333%2c334%2c336%2c337%2c338%2c339%2c340%2c342%2c343%2c344%2c345%2c346%2c347%2c348%2c349%2c350%2c351%2c352%2c353%2c354%2c358%2c359%2c360%2c361%2c362%2c363%2c364%2c365%2c366%2c367%2c368%2c369%2c370%2c371%2c372%2c373%2c374%2c375%2c377%2c378%2c379%2c380%2c381%2c382%2c383%2c384%2c385%2c386%2c387%2c388%2c389%2c390%2c392%2c393%2c394%2c395%2c396%2c397%2c398%2c399%2c400%2c401%2c402%2c404%2c405%2c406%2c407%2c408%2c409%2c410%2c411%2c415%2c416%2c417%2c418%2c419%2c420%2c421%2c422%2c423%2c424%2c425%2c427%2c428%2c429%2c430%2c431%2c432%2c433%2c434%2c435%2c437%2c438%2c439%2c440%2c441%2c442%2c443%2c444%2c445%2c446%2c448%2c449%2c450%2c451%2c452%2c453%2c454%2c455%2c456%2c457%2c458%2c459%2c460%2c461%2c462%2c464%2c465%2c466%2c467%2c468%2c469%2c470%2c471%2c472%2c473%2c474%2c475%2c476%2c477%2c478%2c479%2c480) as a CSV file named `Population Mid-2015.csv`

Columns are:
 - Location: country name
 - Location Type: Country
 - TimeFrame: Mid-2015
 - Data Type: Number
 - Data: population
 
### License of the source data and terms of use

1. Wikipedia article dataset is licenced under the CC-BY-SA 4.0 license.

For more information on this License, check [CC-BY-SA 4.0 license](https://creativecommons.org/licenses/by-sa/4.0/legalcode)

2. Wikimedia's [Privacy Policy](https://wikimediafoundation.org/wiki/Privacy_policy) and [Terms of Use](https://wikimediafoundation.org/wiki/Terms_of_Use/en)

3. Figshare [Privacy Policy](https://figshare.com/privacy) and [Terms of Use](https://figshare.com/terms)

4. Population Research Bureau [Privacy Policy](http://www.prb.org/DataFinder/Topic/~/link.aspx?_id=11A2A1677D184053936CE705FAEDEC1D&_z=z)

### Copyright
The population dataset was downloaded from Population Research Bureau. Copyright © 2016, Population Reference Bureau. All rights reserved.

### Special considerations of data
- `page_data.csv`
1. Country codes are inconsistent.
2. The actual recursion only went 2 levels deep into the category tree. For example, someone listed as an Antiguan politician is included. However, someone exclusively listed as an Antiguan politician who was assassinated is not.

## API documentation
A Wikimedia API endpoint for a machine learning system called ORES needs to be used in order to get article quality predictions.

Documentaions and more information of ORES can be found [here](https://www.mediawiki.org/wiki/ORES)

To avoid hitting limits in ORES, you may want to split revision IDs into chunks (for example: chunks of 50 or 100), pass each chunk to ORES and then stitch the whole set together.

There's an example of reponses from ORES:
![hcds-a2-1](https://user-images.githubusercontent.com/26759376/32299402-b7d1ff3e-bf12-11e7-8ce3-cfce8995bf0e.PNG)


Check Jupyter Notebook file `hcds-a2-bias.ipynb` to see how to use this API.


## Final data file description
** Note: either the population dataset does not have an entry for the equivalent Wikipedia country, or vice versa. Rows that do not have matching data need to be removed.** 

After combining the datasets, there are five fields in the final data file `final_data.csv`:

* country: country name
  * Field Type: String
* article_name: title of policital article
  * Field Type: String
* revision_id：edit ID of the last edit to the page
  * Field Type: Integer
* article_quality: quality of article, each article is assigned in one of six categories:

  FA - Featured article
  
  GA - Good article
  
  B - B-class article

  C - C-class article

  Start - Start-class article

  Stub - Stub-class article
  * Field Type: String
  
* population: populations of a variety of countries
  * Field Type: String - numbers are encoded with commas






## Writeup
Please check the notebook.
