# **The Drupal Dataset**

## Summary 
We present the Drupal dataset, a collection of real-world data extracted from the git repository, the issue tracking system and the official documentation of the popular open-source framework Drupal. We collected extensive non-functional data including faults in different versions of Drupal modules (e.g., 3,392 faults in Drupal v7.23), changes made in the code (e.g., 557 commits) or number of tests and assertions in the modules (e.g., 352 and 24,152, respectively). Additionally, we provide the Drupal feature model, as a representation of the framework configurability, with more than 2000 millions of different Drupal configurations; the largest attributed feature model published so far. Previous evaluations, showed positive correlations among the data collected in the Drupal dataset presented in this paper and their effectiveness at accelerating the detection of faults in Highly-configurable systems. Drupal dataset has become a helpful feedback to researchers and practitioners in the field of variability as well as to serve as a pool of information that helps conduct more realistic experiments and evaluations of Highly-configurable systems. A fact that is evidenced by more than 125 recorded citations since its publication in 2014.
In particular, the Drupal dataset provide the following data: 

### Drupal Feature model
According to the Drupal documentation, each module that is installed and enabled in the system adds a new feature to the framework. Thus, we propose modelling Drupal modules as features of the feature model. Also, when a module is installed, new subfeatures can be enabled adding extra functionality to the module. These features are considered as children features of the module that contains them. The Drupal core modules that must be always enabled are represented as mandatory relations in the feature model. On the other side, all the modules that can be optionally installed and enabled in the system are modelled as optional features in the model. In addition to this, Drupal modules can have dependencies with other modules, i.e. modules that must be installed and enabled for another module to work properly. These dependencies are modelled as cross-tree constraints in the form of requires in the feature model. 
The Drupal feature model is given in two XML formats: FaMa and SXFM formats.

### Non-functional features
Drupal dataset also reports a number of non-functional attributes of the features selected for the Drupal feature models, namely:
* ***Feature size***. This provides a rough idea of the complexity of each feature and its fault propensity. The size of a feature was calculated in terms of the number of lines of code (LoC). 
* ***Cyclomatic Complexity (CC)***. This metric reflects the total number of independent logic paths used in a program and provides a quantitative measure of its complexity. We used the open-source tool phploc to compute the CC of the source code associated with each Drupal feature. Roughly speaking, the tool calculates the number of control flow statements (e.g. “if”, “while”) per lines of code. 
* ***Number of tests***. We provide the total number of test cases and test assertions of each Drupal feature obtained from the output of the SimpleTest module.
* ***Number of reported intallations***. This depicts the number of times that a Drupal feature has been installed as reported by Drupal users. This data was extracted from the Drupal website [10] and could be used as an indicator of the popularity or impact of a feature. 
* ***Number of developers***. We collected the number of developers involved in the development of each Drupal feature. This could give us information about the scale and relevance of the feature as well as its propensity to faults related to the number of people working on it. This information was obtained from the website of each Drupal module as the number of committers involved. 
* ***Number of changes***. Changes in the code are likely to introduce faults. Thus, the number of changes in a feature may be a good indicator of its error proneness and could help us to predict faults in the future. To obtain the number of changes made in each feature, we tracked the commits to the Drupal Git repository.

All this information is recorded in a CSV File containing the Drupal modules considered in the dataset and, for each module, its size, the cyclomatic complexity of its code, the number of test cases and assertions, the number of reported installations, the number of commits made in Drupal versions v7.22 and v7.23, and the number of faults recorded in Drupal v7.22 and v7.23.

### Faults in Drupal
The Drupal dataset collects the number of faults reported in the Drupal features. The information was obtained from the issue tracking systems of Drupal and related modules. We used the web-based search tool of the issue systems to filter the bug reports by severity, status, date, feature name and Drupal version. The search was narrowed by collecting the bugs reported in a period of two years and in two consecutive Drupal versions, v7.22 and v7.23, to achieve a better understanding of the evolution of a real system and to enable test validations based on fault history. Then, the search was refined to eliminate the faults not accepted by the Drupal community, those classified as duplicated bugs, non-reproducible bugs and bugs working as designed. Additionally, we identified and classified the faults into single (those caused by a Drupal model) and integration faults (those caused by the interaction of several modules). 

The Drupal faults are given in a CSV file containing for each Drupal module the number of collected faults classified by type (single or integration faults), severity (minor, normal, major and critical) and by Drupal version (v7.22 and v7.23).
