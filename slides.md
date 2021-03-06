## Evaluating the Quality of Drupal Modules

<div style="font-size: 0.8em">
    <h6>Applying data mining techniques to discover relationships between module metrics and popularity</h6>

    <h6>[ben-denham.github.io/drupal-meetup-module-popularity](https://ben-denham.github.io/drupal-meetup-module-popularity)</h6>
</div>



## Background and Motivation

* Core problem: Is this module of acceptable quality? <!-- .element: class="fragment" -->
* Important without project applications <!-- .element: class="fragment" -->
* DA is looking for ways to indicate module quality: <!-- .element: class="fragment" -->
    * Module "stars"
    * Source-code quality reports


## Background and Motivation

* Previous studies have applied data mining to identify attributes of
  popular software projects
* I decided to use this approach to find relationships between module
  popularity and: <!-- .element: class="fragment" -->
    * Source-code metrics
    * Project metrics considered in practice by surveyed Drupal
      developers
* Popularity would be quantified as the total number of module
  installations <!-- .element: class="fragment" -->



## Collecting the Data

![Collecting the data](images/scraping.gif)


## Building a Module Dataset

* Scraping project pages with Python's BeautifulSoup
* Running PHPDepend and PHPCodeSniffer to generate source-code metrics
* Collected data for ~13,000 Drupal 7 modules over ~60 hours


## Tips for Web-Scraping

* Check website rate limits <!-- .element: class="fragment" -->
* Ensure it won't crash overnight <!-- .element: class="fragment" -->
* Scrape some pages, correct bugs, repeat <!-- .element: class="fragment" -->
* Make it easy to pause/resume <!-- .element: class="fragment" -->
* LOG ALL THE THINGS! <!-- .element: class="fragment" -->



## "Cleaning" the Data

!["Cleaning" the data](images/cleaning.gif)


## "Cleaning" the Data

Argued to be the most important step for successful data mining

* Normalising source-code metrics to the size of the codebase <!-- .element: class="fragment" -->
* Removing "young" projects <!-- .element: class="fragment" -->
* Removing metrics directly-related to popularity <!-- .element: class="fragment" -->


## Classifying Modules

| Label | Total Installations | Modules |
| ----- | ------------------- | ------- |
| Unpopular | < 100 | 5,414 |
| Moderate | > 100 & < 10,000 | 4,291 |
| Popular | > 10,000 | 510 |



## Machine Learning

![Machine learning](images/machine-learning.gif)


## Machine Learning

* Machine Learning != Artificial Intelligence
    * Machine learning algorithms "learn" from a dataset to reveal
      patterns in the data <!-- .element: class="fragment" -->
* Best approach: classification algorithms <!-- .element: style="font-size: 90%;" class="fragment" -->
    * Input: Module records labeled with popularity "class"
    * Output: Classifier to predict the popularity of a module
        * Constrained to "interpretable" classifiers <!-- .element: class="fragment" -->


## Classification Algorithms

* RIPPER - Classification rules <!-- .element: class="fragment" -->
    * Rules for assigning a class based on attributes
* C4.5 - Decision tree <!-- .element: class="fragment" -->
    * A tree branches on attribute values to arrive at a class
      assignment "leaf"
* Na&iuml;ve Bayes <!-- .element: class="fragment" -->
    * Uses Bayesian probability to weight the importance of
      attribute values for assigning a class


## Classifier Optimization

* Experiments were performed to optimise:
    * Attribute selection <!-- .element: class="fragment" -->
    * Class balancing <!-- .element: class="fragment" -->
    * Algorithm parameters <!-- .element: class="fragment" -->
* The best results were achieved when "moderately popular" modules
  were removed from the dataset <!-- .element: class="fragment" -->



## The Results!


## Popular Modules...

* Have a Drupal 8 version <!-- .element: style="font-size: 80%;" -->
* Have >= 3 maintainers <!-- .element: style="font-size: 80%;" -->
* Have documentation pages <!-- .element: style="font-size: 80%;" -->
* Have automated tests <!-- .element: style="font-size: 80%;" -->
* Have a recommended release <!-- .element: style="font-size: 80%;" -->
* Have > 11% translation progress <!-- .element: style="font-size: 80%;" -->
* Have a description > 1600 characters long <!-- .element: style="font-size: 80%;" -->
* Have had a commit in the last 4 months <!-- .element: style="font-size: 80%;" -->
* **Have releases > 70 days apart** <!-- .element: style="font-size: 80%;" -->
* **Have cyclomatic complexity > 100** <!-- .element: style="font-size: 80%;" -->
* **Have a root/child class ratio between 0.25% and 30%** <!-- .element: style="font-size: 80%;" -->


## Analysis

* Aligned with the ISO25010 software-quality model <!-- .element: class="fragment" -->
    * "Reliability" strongly related to popularity
* Popular modules did not have better source-code metrics <!-- .element: class="fragment" -->



## Limitations

![Limitations](images/limitations.gif)


## Limitations

* No directionality in the identified relationships
* High installation count != well-engineered <!-- .element: class="fragment" -->
* Various project attributes were impractical to consider <!-- .element: class="fragment" -->



## Implications for the Drupal Community

* Will software-metric reports be useful for Drupal? <!-- .element: class="fragment" -->
    * Do they indicate quality for Drupal code? <!-- .element: class="fragment" -->
    * Are many popular modules poor-quality? Does it matter? <!-- .element: class="fragment" -->
    * At least: community strength indicates project success much more
      than source-code metrics <!-- .element: class="fragment" -->
* A module evaluation tool for project pages? <!-- .element: class="fragment" -->


## Module Evaluation Tool

![Proposed module evaluation tool presenting colour-coded metric values](images/colour-scale.png) <!-- .element: style="border: none;" -->



## What Next?

* Testing and trialling a module evaluation tool <!-- .element: class="fragment" -->
* Tracking the progression of metrics and popularity over time to determine
  relationship directionality <!-- .element: class="fragment" -->
* Training classifiers according to expert qualitative analysis <!-- .element: class="fragment" -->
* Further analysis of the module dataset <!-- .element: class="fragment" -->



## Thanks!

Any questions or thoughts?

Gifs from [Devops Reactions](http://devopsreactions.tumblr.com)
