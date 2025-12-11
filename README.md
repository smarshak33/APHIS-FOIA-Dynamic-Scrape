# APHIS FOIAs Dynamic Scrape and Text Analysis
Goal: download, scrape, and analyze all FOIA documents in the USDA's APHIS repository for mentions of keywords for my capstone investigative project. The data used in this analysis comes from[ APHIS FOIA logs](url). 
## Dynamic Scrape
For the dynamic scrape, I found the url hidden in the Network < FetchXHR inspection tool for developers, since the code was not available on the page. It led me to a csv file as the source where the FOIAs were stored. Because my goal was to download all 139 pdfs, I needed to clean up the "Title" column because it included the a href tag from the code which would prevent me from downloading. Using a lambda function, I created a new column with just the pdfs. I then used another lambda function to download the files. However, it froze after downloading 107 files, so I had to build another function to extract the remaining 37 without repeating my previous downloads. Once all 139 files were downloaded, I put them in a folder called "pdfs."
## Text analysis
The notebook produces the following files:
* [APHIS FOIA Keywords.csv](url)

For the text analysis portion, I inputted all the necessary libraries and created a list of keywords. I then created a test folder of three pdfs; two which contained the pdfs and one which did not. I created a for loop iterating through the files using both MangoCR to use OCR on the pdfs and Fuzzy Context Finder to find matches or near matches of my keywords. When that was successful, I repeated the same steps on 20 documents as a proof of concept, turned it into a dataframe with tabular2text, and downloaded my results as a csv.
