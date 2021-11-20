# CSE6242_Team181_Amazon
Final Project for CSE6242 - Amazon Co-Purchasing Network Graph

# Overview



## Data Processesing
1. Download the Product Category you wish to use from the Amazon review data (2018) website:
http://deepyeti.ucsd.edu/jianmo/amazon/index.html
2. Use the Jupyter Notebook: Amazon_Data_Explore to examine the dataset and get familiar with its structure
3. Manipulate the DataSet to generate an edgelist consisting of Amazon Product Level ID (ASIN) to each associated co-purchased (Also-Buys)
4. Join in the Label (Item Description) for all ASIN's outside of the base category.
5. Remove any items without a label, which correspondes to items with 0 reviews (don't exist in dataset)
6. Export this final Node + Edgelist to CSV.

## Graph Input
1. Use the Jupyter Notebook Generate_Graphy.ipynb to create the network graph
2. Input the CSV from the Data Processing Steps above
3. 
