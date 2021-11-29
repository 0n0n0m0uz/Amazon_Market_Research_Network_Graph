## Final Project for Team 181 - CSE6242 - Amazon Co-Purchasing Network Graphing Tool

We designed a tool for aspiring entrepreneurs seeking to get involved with Amazon FBA or have a side hustle.  It is very overwhelming for people to know where to being.  We saw a need for a tool that could take advantage of publicly available Amazon Co-Purchasing datasets.  By allowing users to select a produuct category of interest and drill down into deeper layers of granularity they may discover product niches, relationships between products they were not aware existed, or groups of products commonly purchased together.




<p float="center">
 <img src="https://github.com/0n0n0m0uz/CSE6242_Team181_Amazon/blob/main/images/maximal_cliques2.jpg"/>
 <img src="https://github.com/0n0n0m0uz/CSE6242_Team181_Amazon/blob/main/images/LeidenImg.png"/>
</p>

# tl;dr 
download/git pull onto your machine to view the webpage with an interactive co-purchasing community graph

# Overview

With any publicly available dataset of this size comes many data quality issues to deal with.  This means there are many manual steps to take to get a clean, duplicate free, base case for futher analysis.  By following the steps outlined in the python notebooks, you will be able to analyze and product categrory available on: 
[Amazon review data](http://deepyeti.ucsd.edu/jianmo/amazon/index.html)

***
## Data processing

The goal of this step is to import Amazon Co-Purchasing data for a single product category, clean up that dataset and get it into a form more useful for our purposes, explore summary statistics to get a feel for the category and finally export a duplicate-free edgeslist which can then be used as input for various graphing tools.

1. Download the datasets for the Product Category you wish to use from the Amazon review data (2018) website:
http://deepyeti.ucsd.edu/jianmo/amazon/index.html
2. Use the Jupyter Notebook: **Amazon_Data_Exploration.ipynb** to import/download the dataset
3. Follow the notebook cells in sequential order to clean the dataset
4. View the summary, data exploration cells to understand the product category at a high-level and discover nodes or products of interest and their co-purchasing associations
5. Export the final category Edgelist to CSV.

### Thought on Dataset
With a public dataset of this size, there are a host of data wrangling tasks to perform to get a clean subeset to create the node/edgelists needed for visualization. The first step was the actual structure of the dataset -- many of the cells contained lists of items instead of a single value. In the most extreme case a particular ASIN had a list of 100 also-bought items, this means the addition of 100 new rows of data.  This proved a challenge to work with even on a powerful Google Cloud Instance.  We had to try several methods, including converting the JSON data to SQL database, Spark Dataframe, etc. Ultimately the technique that we used was to use the 'split' command in BASH terminal to break up the 100GB file into 20 equally sized pieces.  We were then able to load one piece at a time, eliminate all the columns we did not need, and then pickle the file into a byte stream.  We could then concatenate each of the pickles and create a much leaner file whose size did not present resource consumption issues.

In addition to technical issues related to the structure and size of files, there were data integrity issues that also had to be addressed.  Some of these were tricky in that they only revealed themselves over time as we got into deeper granularity and actually started to visualize the data.  The primary issue were duplicate items, however they were not duplicates in the traditional sense of being identical.  The product numbers were different however the items were the same as revealed by the metadata descriptions.  Without being an Amazon employee we hypothesized that they must recycle sku numbers over time, perhaps as new versions of a product comes out.  For the purposes of our graphing and clustering analysis, this directly affected the results because the algorithms were clustering products together that were identical for all intents and purposes. We also ran into limitation with the data, specifically a case where metadata did not exist for every single also-buy, we discoverd the reason for this is these products did not contain a review in the dataset.  These rows therefore had to be eliminated changing the overall interpretation of all results to "Products that have been reviewed at least once".

***
## Graph Input

The goal of this step is to take your category edgelist from above and import it into the networkx graphing package.  By using this jupyter notebook you can apply various community-detection algorithms and other high level graph metrics.  The final step will output the graph to a .gexf package which can be used to plot the graph in GEPHI graphing software.

1. Use the notebook **GraphBuild.ipynb** to input the CSV from the Data Processing Steps above
2. Use networkx to create various graphs and run various community detection algorithms, including Louvain, Lediden, Girvan Groups
3. Find Cliques of interest, Graph Components and partitions to try and discover things about the category
4. Export graph to .gexf

## View Graph Visualization in Gephi (or other software)


