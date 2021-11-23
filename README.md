## Final Project for Team 181 - CSE6242 - Amazon Co-Purchasing Network Graphing Tool

We designed a tool for aspiring entrepreneurs seeking to get involved with Amazon FBA or have a side hustle.  It is very overwhelming for people to know where to being.  We saw a need for a tool that could take advantage of publicly available Amazon Co-Purchasing datasets.  By allowing users to select a produuct category of interest and drill down into deeper layers of granularity they may discover product niches, relationships between products they were not aware existed, or groups of products commonly purchased together.


<p align="center">
  <img src="https://github.com/0n0n0m0uz/CSE6242_Team181_Amazon/blob/main/images/LeidenImg.png" align="left"/>
  <img src="https://github.com/0n0n0m0uz/CSE6242_Team181_Amazon/blob/main/images/maximal_cliques2.jpg" align="right"/>
</p>

***
<br>
<br>

# tl;dr 
download/git pull onto your machine to view the webpage with an interactive co-purchasing community graph

# Overview

With any publicly available dataset of this size comes many data quality issues to deal with.  This means there are many manual steps to take to get a clean, duplicate free, base case for futher analysis.  By following the steps outlined, you will be able to analyze and product categrory available on: 
[Amazon review data](http://deepyeti.ucsd.edu/jianmo/amazon/index.html)

***
## Data processing

The goal of this step is to import Amazon Co-Purchasing data for a single product category, clean up that dataset and get it into a form more useful for our purposes, explore summary statistics to get a feel for the category and finally export a duplicate-free edgeslist which can then be used as input for various graphing tools.

1. Download the datasets for the Product Category you wish to use from the Amazon review data (2018) website:
http://deepyeti.ucsd.edu/jianmo/amazon/index.html
2. Use the Jupyter Notebook: **Amazon_Data_Exploration.ipynb** to import/download the dataset
3. Follow the notebook cells in sequential order to clean the dataset
4. View the summary, data exploration cells to understand the product category at a high-level
5. Export the final category Edgelist to CSV.

***
## Graph Input

The goal of this step is to take your category edgelist from above and import it into the networkx graphing package.  By using this jupyter notebook you can apply various community-detection algorithms and other high level graph metrics.  The final step will output the graph to a .gexf package which can be used to plot the graph in GEPHI graphing software.

1. Use the notebook **GraphBuild.ipynb** to input the CSV from the Data Processing Steps above
2. Use networkx to create various graphs and run various community detection algorithms, including Louvain, Lediden, Girvan Groups
3. Find Cliques of interest, Graph Components and partitions to try and discover things about the category
4. Export graph to .gexf

## View Graph Visualization in Gephi (or other software)


