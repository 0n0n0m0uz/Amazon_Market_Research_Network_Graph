# CSE6242_Team181_Amazon

## Final Project for CSE6242 - Amazon Co-Purchasing Network Graph

We designed a tool for aspiring entrepreneurs seeking to get involved with Amazon FBA or have a side hustle.  It is very overwhelming for people to know where to being.  We saw a need for a tool that could take advantage of publicly available Amazon Co-Purchasing datasets.  By allowing users to select a produuct category of interest and drill down into deeper layers of granularity they may discover product niches, relationships between products they were not aware existed, or groups of products commonly purchased together.


<p align="center">
  <img src="https://github.com/0n0n0m0uz/CSE6242_Team181_Amazon/blob/main/images/LeidenImg.png"/>
</p>

# Overview

With any publicly available dataset of this size comes many data quality issues to deal with.  This means there are many manual steps to take to get a clean, duplicate free, base case for futher analysis.  By following the steps outlined, you will be able to analyze and product categrory available on: 
![Amazon review data](http://deepyeti.ucsd.edu/jianmo/amazon/index.html)


## Data Processesing
1. Download the Product Category you wish to use from the Amazon review data (2018) website:
http://deepyeti.ucsd.edu/jianmo/amazon/index.html
2. Use the Jupyter Notebook: Amazon_Data_Exploration notebook to examine the dataset and get familiar with its structure
3. Manipulate the DataSet to generate an edgelist consisting of Amazon Product Level ID (ASIN) to each associated co-purchased (Also-Buys)
4. Join in the Label (Item Description) for all ASIN's outside of the base category.
5. Remove any items without a label, which correspondes to items with 0 reviews (don't exist in dataset)
6. Export this final Node + Edgelist to CSV.

## Graph Input
1. Use the Jupyter Notebook Generate_Graphy.ipynb to create the network graph
2. Input the CSV from the Data Processing Steps above
3. 
