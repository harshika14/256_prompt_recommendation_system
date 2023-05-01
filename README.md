# 256_prompt_recommendation_system
This repository is created for prompt recommendation system

## 0_Data_Downloader.ipynb
This file was initially created in Google Colab.  
The link of Google Colab is [here](https://colab.research.google.com/drive/1Xc0dKId8Gu4lSssxiMVdtHXpgb9GJ6Gy?usp=sharing)  
The purpose of this notebook was to download [the datase](https://github.com/poloclub/diffusiondb) using Hugging Face Downloader, save the data as a csv file, and save images in local directory. 

To reproduce the same result, change a working directory appropriately.  

## 1_Data_Preprocessing.ipynb
This file was initially created in Google Colab.  
The link of Google Colab is [here](https://colab.research.google.com/drive/1OH_yvckOC7AOAkl--geJyE-rtjjCY5lc?usp=sharing)  
The purpose of this notebook was to preprocess prompts. The text preprocessing includes removing or converting emoji(s) to texts, removing numeric and stopwords, and applying stemming (PoterStemming is used).  

To reproduce the same result, download "prompt_with_img_path.csv" under Data folder. Also, image_path column should be modified appropriately to access images.   

## 2_Baseline_Model1.ipynb
This file was initially created in Google Colab.  
The link of Google Colab is [here](https://colab.research.google.com/drive/1m0H-dxdkNYito-9h2XKiAfQnPoUO11Lg?usp=sharing)   
The purpose of this notebook was to build a algorithm that recommends simialr prompts and corresponding images in the dataset without any state-of-art embedding methods.   

To reprodce the same result, download "prompt_with_img_path.csv" and "clean_text_only.csv" under Data folder. Also, image_path column should be modified appropriately to access images.  

## 5_Create_Graphs.ipynb
This file was initially created in Google Colab.  
The link of Google Colab is [here](https://colab.research.google.com/drive/1ZrOkjHNnndLvZX9Lig2tz5vztBUIEdSl?usp=sharing)   
The purpose of this notebook was to save a networkx graph as a gexf file format for each algorithm. Firstly, similarity matrix was required. Secondly, a graph is created with a threshold of 0.7 where threshold represents the minimum similarity score that creates an edge between nodes. A node in the graph represents a prompt. There are links between nodes when a similarity score is greater or equal to the threshold. Gephi software was used to visualizae and analyze graphs.

### How to use Gephi software for the project
1. Download Gephi software from [this link](https://gephi.org/users/download/). The tutorial link is also available in [here](https://gephi.org/tutorials/gephi-tutorial-quick_start.pdf). 
2. Open Gephi software and then open a gexf file.
3. Open 'Statistic' window to calculate average degree, average weighted degree, graph density, and average clustering coefficient. 
4. Run 'Modularity' under commnity detection. The default setting was used where the setting was it's randomized, used weights, resolution of 1 and classes start at 0. Gephi implements the Louvain method for community detection as it's described in the tutorial.
5. Go to Appearance tab > Nodes > Partition module. Then, choose an attribute as modularity class to color nodes by their communities.
6. Click the setting for the size of nodes. Go to Appearance tab > Nodes > Ranking. Then, choose an attribute as degree to differenciate each node size by its degree. The min and max sizes of node was varied depending on gragh's density, the number of nodes, and the number of edges. 
7. Go to Layout and then choose random layout with sapce size of 1000 and then hit run button.
8. Then, in the same "Layout" tab, choose Yifan Hu Proporational layout and then play with optimal distance to obtain the desirable graph layout. It might create clusters with the same community, which is what we want.
9. If some communities were scattered, manually drag each node to create a cluster with the same node colors.
10. Go to 'Preview' tab and then select show labes with font size of 4 in Preview setting. Then, click the refresh button. Then, export the graph as pdf file. The exporting was failed for graphs that have high density due to lack of memory. For those graphs, screen shot was done, which has much lower quality than pdf file.






