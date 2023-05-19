# 23_Summer_School_Balsz
Allocating students to classes / teachers based on EOY assessments.

## Overview
The purpose of this analysis is to place Summer School students into classes based on their performance in Math and Reading on the NWEA End-of-Year (EOY) assessment and to choose which standard(s) should be focused on in each grade-subject combination. The goal is to group students into classrooms that will focus on specific standards based on those students' needs. The specific focus is necessary due to the small number of instructional days during Summer School and because targeted instruction will theoretically increase each student's opportunity to improve in their specific area(s) of need.

Classes will be constructed for Math and Reading separately. Each student will be placed into two classes, each meeting for half of a school day. Students will be placed based on their individual needs and thus may be in different classrooms for Math and Reading. That is, a student may or may not have the same teacher for both classes. Each teacher will be provided with a specific focus (set of standards) that correspond to the needs of the students placed in the class for each subject.

In order to create maximally homogenous groups for each classroom, students cannot merely be placed in a class based on their lowest GoalRitScore from the NWEA EOY assessment. This creates two potential difficulties: 1) drastically varied class sizes, and 2) a lack of homogeneity of student ability beyond a given GoalRitScore being each student's lowest score. That is, just because a set of students in the same grade each scored lowest in Goal 1, that does not ensure any further commonality among those students. A more robust assignment method is required to maximize the potential benefits of Summer School instruction for these students.

Note that due to FERPA, no identifiable data will be shared in this repository. 

## Resources
* R version 4.2.2
* RStudio version 2023.03.0 Build 386
* Data downloaded 18 May 2023 from NWEA Map Growth

The following R packages were used:
* tidyverse
* flextable
* anticlust
* cluster
* factoextra
* gridExtra
* janitor

## Clustering Method
Various clustering methods were considered for this task, including KMeans clustering, K-Medoids, Hierarchical Clustering, and Anticlustering. In order to determine the best clustering methodology for our purposes, and given the limited timeframe between EOY testing and Summer School, a sample set, consisting of all Grade 4 students (n = 51), was used to assign students to classes (groups) utilizing the four mentioned clustering methods.

(Aggregated data to be presented as necessary - shortly)

### Simplified explanation of clustering methods
KMeans and K-Mediods function similarly in that data are presented like a scatterplot in a multidimentional space. For Kmeans, the algorithm picks a predetermined number of point on this scatterplot at random and computes the mean distance of every data point to one of those points. The predetermined number of points in our case is the number of Grade 4 teachers teaching in Summer School. The algorithm repeats this process a number of times, then selects the set of points which has the smallest mean distance to between those points and the data points. This results in grouping all datapoints into a group based on their proximity to one of the points, and those groups are numbered 1 to K (number of teachers). For K-Mediod, the methodology is the same except that the algorithm, instead of randomly generating a point, selects one of the datapoints as a "median" datapoint. The K-Mediod algorithm then computes the mean distance, repeats the process, then selects the best set, which provides the theoreticaly best grouping.
