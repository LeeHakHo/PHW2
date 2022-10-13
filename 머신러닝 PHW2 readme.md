# For Quick View

[AutoML(scaler\_list, encoder\_list, model\_list, dataset) 1](#_Toc115720954)

[Evaluation Result:: 3](#_Toc115720955)

[Our Work 10](#_Toc115720957)

[Problems 10](#_Toc115720958)

[Future Work 11](#_Toc115720959)

[**Contribution** 12](#_Toc115720961)




# AutoML(scaler\_list, encoder\_list, model\_list, dataset)

AutoML – Requires a list of scalers, a list of encoders, a list of clustering models and dataset. Outputs the best result for data clustering using various scaler, encoder, model combinations.

 **Parameters::** 
 **scaler\_list : _list, default = [StandardScaler(), RobustScaler(), MinMaxScaler(), Normalizer(), MaxAbsScaler()]_**The list of scaler user wants to test. The function will return the test of combination that used corresponding scaler. It will show you the kind of combination that shows the best result of the program (Auto ML) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.001.png)
 
**encoder\_list : _list, default = [OneHotEncoder(), LabelEncoder()]_**The list of encoder user wants to test. The function will return the test of combination that used corresponding encoder. It will show you the kind of combination that show the best result of the program (Auto ML) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.002.png)

**model\_list : _list, default = [KMeans(), GaussianMixture(), DBSCAN(), OPTICS()]_**The list of model user wants to test. The function will return the test of combination that used corresponding model. It will show you the kind of combination that show the best result of the program (Auto ML) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.003.png)

**dataset : _data file, default = housing.csv_** The data file user wants to test. Such as 'The California Housing Prices Dataset'. You should drop the target feature before putting it in as a parameter.

 **Examples::** 
 ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.004.png)
 

# **Evaluation Result**
 
 ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.005.png) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.006.png) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.007.png) ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.008.png)
 ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.009.png)

|Last three results are the results of the second loop. As the above evaluation result shows, second iteration has better quality than the first result.
 ![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.010.png)
**[KMeans when k=2]****Above plot is kmeans for all 13 attributes (including encoded 'ocean\_proximity'). We can tell that feature 'total\_room, total\_bedroom, population, household' shows more distinctive clustering than other features. They are influential to the clustering result.**Also, by the scattered graph above, we can see those 4 features are proportional.
 

# **Our Work**
 


- We focused on making a general giant function for clustering.
- We made data preprocessing process such as Scaling/Encoding to be run in the function.
- We tested for all kind of combinations we could get. (Combinations of scaler + encoder + clustering algorithm).
- For the quality measure tools, since we wanted to test the result in various way, we used additional quality measure tools and did our own little active learning.
- We tested both original dataset and the modified version dataset which doesn't include longitude and latitude.

 

# **Problems**
 


- Each algorithm has a different method of clustering, encoding, and scaling.
- We couldn't consider every possible parameters/quality measure tools since there were too many of them.
- Some algorithms cannot measure the result or require the user to check the result for best results (such as DBSCAN which does not support prediction).
- CLARANS module isn't supported by sklearn, we had to make the function. However, CLARANS required different modeling type. We had difficulties in putting CLARANS as a input with other algorithms.
- Combining these different algorithms into one big function (AutoML) requires a lot of exception handling.
- Because we used a pipeline for the implementation, it required more restrictions than implementing everything individually. (We suffered from the error for applying 'LabelEncoder').
- Building/Compiling took a lot of time which made harder for us to test and complete the function.

 

# **Future Work**
 


- Clustering functions for each algorithm (calling individual functions from AutoML might be more efficient than putting it all together) as well as encoding, scaling and plot output
- Learn deeper about quality measure tools and feel the actual difference of various tools.
- Complete CLARANS algorithm
- Implement a pipeline which 'LabelEcoder' can also be applied
- A better large function (AutoML) can be constructed by grouping compatible algorithms in a large category to derive results, and by classifying the exceptions separately and deriving each result.

 

# **Conclusion**
 

Since we don't know how many groups (clusters) we need, how well we did the clustering, clustering is very difficult. We have to try every possible combination and analyze through your own eyes. Even with the same clustering results, we can't say it's good or bad because it depends on the purpose of the application and the feature of the dataset. Still, we try to find the best clustered result so that we can use the information and make a better decision of our own.

By implementing the clustering giant function, we learned the difference between classification and clustering. Plus, we spent a lot of time thinking about the purpose of this data clustering. Who would want to use this? When can we use it?

We think this type of questions are essential for the ones who handle data. It was a valuable experience which we wouldn't know if we hadn't tried it on our own.
