
# For Quick View
[AutoML(scaler_list, encoder_list, model_list, dataset)	1](#_Toc115720954)

[Evaluation Result::	3](#_Toc115720955)

[Our Work	10](#_Toc115720957)

[Problems	10](#_Toc115720958)

[Future Work	11](#_Toc115720959)

[**Contribution**	12](#_Toc115720961)



||
| :- |
|<p></p><p><h1>**AutoML(scaler\_list, encoder\_list, model\_list, dataset)**</h1></p><p></p>|
|<p></p><p>AutoML – Requires a list of scalers, a list of encoders, a list of clustering models and dataset. Outputs the best result for data clustering using various scaler, encoder, model combinations. </p><p></p>|
|**Parameters::**|
|<p>**scaler\_list : *list, default = [StandardScaler(), RobustScaler(), MinMaxScaler(), Normalizer(), MaxAbsScaler()]***</p><p>The list of scaler user wants to test. The function will return the test of combination that used corresponding scaler. It will show you the kind of combination that shows the best result of the program (Auto ML)</p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.001.png)</p><p></p><p>**encoder\_list : *list, default = [OneHotEncoder(), LabelEncoder()]***</p><p>The list of encoder user wants to test. The function will return the test of combination that used corresponding encoder. It will show you the kind of combination that show the best result of the program (Auto ML)</p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.002.png)</p><p></p><p>**model\_list : *list, default = [KMeans(), GaussianMixture(), DBSCAN(), OPTICS()]***</p><p>The list of model user wants to test. The function will return the test of combination that used corresponding model. It will show you the kind of combination that show the best result of the program (Auto ML)</p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.003.png)</p><p></p><p>**dataset : *data file, default = housing.csv***</p><p>The data file user wants to test. Such as ‘The California Housing Prices Dataset’. You should drop the target feature before putting it in as a parameter.</p><p></p>|
|**Examples::**|
|<p>![텍스트이(가) 표시된 사진

자동 생성된 설명](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.004.png)</p><p></p>|
|<h1>**Evaluation Result**</h1>|
|<p>![텍스트이(가) 표시된 사진

자동 생성된 설명](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.005.png)</p><p>![텍스트이(가) 표시된 사진

자동 생성된 설명](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.006.png)</p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.007.png)</p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.008.png)</p><p></p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.009.png)</p><p>**Last three results are the results of the second loop. As the above evaluation result shows, second iteration has better quality than the first result.**</p><p></p><p>![](Aspose.Words.9aca9a90-76ee-47c0-adbd-4e04b00d74b9.010.png)</p><p></p><p>[KMeans when k=2]</p><p>Above plot is kmeans for all 13 attributes (including encoded ‘ocean\_proximity’). We can tell that feature ‘total\_room, total\_bedroom, population, household’ shows more distinctive clustering than other features. They are influential to the clustering result.</p><p>Also, by the scattered graph above, we can see those 4 features are proportional. </p><p></p>|
|<h1>**Our Work**</h1>|
|<p></p><p>- We focused on making a general giant function for clustering. </p><p>- We made data preprocessing process such as Scaling/Encoding to be run in the function.</p><p>- We tested for all kind of combinations we could get. (Combinations of scaler + encoder + clustering algorithm).</p><p>- For the quality measure tools, since we wanted to test the result in various way, we used additional quality measure tools and did our own little active learning.</p><p>- We tested both original dataset and the modified version dataset which doesn’t include longitude and latitude.</p><p></p>|
|<h1>**Problems**</h1>|
|<p></p><p>- Each algorithm has a different method of clustering, encoding, and scaling. </p><p>- We couldn’t consider every possible parameters/quality measure tools since there were too many of them.</p><p>- Some algorithms cannot measure the result or require the user to check the result for best results (such as DBSCAN which does not support prediction).</p><p>- CLARANS module isn’t supported by sklearn, we had to make the function. However, CLARANS required different modeling type. We had difficulties in putting CLARANS as a input with other algorithms.</p><p>- Combining these different algorithms into one big function (AutoML) requires a lot of exception handling.</p><p>- Because we used a pipeline for the implementation, it required more restrictions than implementing everything individually. (We suffered from the error for applying ‘LabelEncoder’).</p><p>- Building/Compiling took a lot of time which made harder for us to test and complete the function.</p><p></p>|
|<h1>**Future Work**</h1>|
|<p></p><p>- Clustering functions for each algorithm (calling individual functions from AutoML might be more efficient than putting it all together) as well as encoding, scaling and plot output</p><p>- Learn deeper about quality measure tools and feel the actual difference of various tools.</p><p>- Complete CLARANS algorithm</p><p>- Implement a pipeline which ‘LabelEcoder’ can also be applied</p><p>- A better large function (AutoML) can be constructed by grouping compatible algorithms in a large category to derive results, and by classifying the exceptions separately and deriving each result.</p><p></p>|
|<h1>**Conclusion**</h1>|

Since we don’t know how many groups (clusters) we need, how well we did the clustering, clustering is very difficult. We have to try every possible combination and analyze through your own eyes. Even with the same clustering results, we can’t say it’s good or bad because it depends on the purpose of the application and the feature of the dataset. Still, we try to find the best clustered result so that we can use the information and make a better decision of our own.

By implementing the clustering giant function, we learned the difference between classification and clustering. Plus, we spent a lot of time thinking about the purpose of this data clustering. Who would want to use this? When can we use it?

We think this type of questions are essential for the ones who handle data. It was a valuable experience which we wouldn’t know if we hadn’t tried it on our own.
