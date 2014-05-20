Week1 Notes
========================================================



```r


oldwd = getwd()

setwd("/mnt/hgfs/WorkSpaces/data_science/Getting_and_Cleaning_Data/notes")

```


## down.file example


```r
fileUrl <- "https://data.baltimorecity.gov/api/views/dz54-2aru/rows.csv?accessType=DOWNLOAD"


download.file(fileUrl, destfile = "./data/cameras.csv", method = "curl")

list.files("./data")
```

```
## [1] "cameras.csv"  "cameras.xlsx"
```

```r



dateDownloaded <- date()
dateDownloaded
```

```
## [1] "Tue May 20 23:45:01 2014"
```

```r

```



## Read local file


```r
cameraData <- read.table("./data/cameras.csv", sep = ",", header = TRUE)
head(cameraData)
```

```
##                          address direction      street  crossStreet
## 1       S CATON AVE & BENSON AVE       N/B   Caton Ave   Benson Ave
## 2       S CATON AVE & BENSON AVE       S/B   Caton Ave   Benson Ave
## 3 WILKENS AVE & PINE HEIGHTS AVE       E/B Wilkens Ave Pine Heights
## 4        THE ALAMEDA & E 33RD ST       S/B The Alameda      33rd St
## 5        E 33RD ST & THE ALAMEDA       E/B      E 33rd  The Alameda
## 6        ERDMAN AVE & N MACON ST       E/B      Erdman     Macon St
##                 intersection                      Location.1
## 1     Caton Ave & Benson Ave (39.2693779962, -76.6688185297)
## 2     Caton Ave & Benson Ave (39.2693157898, -76.6689698176)
## 3 Wilkens Ave & Pine Heights  (39.2720252302, -76.676960806)
## 4     The Alameda  & 33rd St (39.3285013141, -76.5953545714)
## 5      E 33rd  & The Alameda (39.3283410623, -76.5953594625)
## 6         Erdman  & Macon St (39.3068045671, -76.5593167803)
```

```r

cameraData2 <- read.csv("./data/cameras.csv")
head(cameraData2)
```

```
##                          address direction      street  crossStreet
## 1       S CATON AVE & BENSON AVE       N/B   Caton Ave   Benson Ave
## 2       S CATON AVE & BENSON AVE       S/B   Caton Ave   Benson Ave
## 3 WILKENS AVE & PINE HEIGHTS AVE       E/B Wilkens Ave Pine Heights
## 4        THE ALAMEDA & E 33RD ST       S/B The Alameda      33rd St
## 5        E 33RD ST & THE ALAMEDA       E/B      E 33rd  The Alameda
## 6        ERDMAN AVE & N MACON ST       E/B      Erdman     Macon St
##                 intersection                      Location.1
## 1     Caton Ave & Benson Ave (39.2693779962, -76.6688185297)
## 2     Caton Ave & Benson Ave (39.2693157898, -76.6689698176)
## 3 Wilkens Ave & Pine Heights  (39.2720252302, -76.676960806)
## 4     The Alameda  & 33rd St (39.3285013141, -76.5953545714)
## 5      E 33rd  & The Alameda (39.3283410623, -76.5953594625)
## 6         Erdman  & Macon St (39.3068045671, -76.5593167803)
```



## Read excel file


```r
fileUrl2 <- "https://data.baltimorecity.gov/api/views/dz54-2aru/rows.xlsx?accessType=DOWNLOAD"


download.file(fileUrl2, destfile = "./data/cameras.xlsx", method = "curl")

list.files("./data")
```

```
## [1] "cameras.csv"  "cameras.xlsx"
```

```r

## install.packages('xlsx')
library(xlsx)
```

```
## Loading required package: rJava
## Loading required package: xlsxjars
```

```r

cameraData3 <- read.xlsx2("./data/cameras.xlsx", sheetIndex = 1, header = TRUE)
head(cameraData3)
```

```
##                          address direction      street  crossStreet
## 1       S CATON AVE & BENSON AVE       N/B   Caton Ave   Benson Ave
## 2       S CATON AVE & BENSON AVE       S/B   Caton Ave   Benson Ave
## 3 WILKENS AVE & PINE HEIGHTS AVE       E/B Wilkens Ave Pine Heights
## 4        THE ALAMEDA & E 33RD ST       S/B The Alameda      33rd St
## 5        E 33RD ST & THE ALAMEDA       E/B      E 33rd  The Alameda
## 6        ERDMAN AVE & N MACON ST       E/B      Erdman     Macon St
##                 intersection                      Location.1
## 1     Caton Ave & Benson Ave (39.2693779962, -76.6688185297)
## 2     Caton Ave & Benson Ave (39.2693157898, -76.6689698176)
## 3 Wilkens Ave & Pine Heights  (39.2720252302, -76.676960806)
## 4     The Alameda  & 33rd St (39.3285013141, -76.5953545714)
## 5      E 33rd  & The Alameda (39.3283410623, -76.5953594625)
## 6         Erdman  & Macon St (39.3068045671, -76.5593167803)
```

```r


## subset xlsx

```


## Read xml


```r

## install.packages('XML')

library(XML)
fileUrl <- "http://www.w3schools.com/xml/simple.xml"
doc <- xmlTreeParse(fileUrl, useInternal = TRUE)
doc
```

```
## <?xml version="1.0" encoding="UTF-8"?>
## <!-- Edited by XMLSpy -->
## <breakfast_menu>
##   <food>
##     <name>Belgian Waffles</name>
##     <price>$5.95</price>
##     <description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
##     <calories>650</calories>
##   </food>
##   <food>
##     <name>Strawberry Belgian Waffles</name>
##     <price>$7.95</price>
##     <description>Light Belgian waffles covered with strawberries and whipped cream</description>
##     <calories>900</calories>
##   </food>
##   <food>
##     <name>Berry-Berry Belgian Waffles</name>
##     <price>$8.95</price>
##     <description>Light Belgian waffles covered with an assortment of fresh berries and whipped cream</description>
##     <calories>900</calories>
##   </food>
##   <food>
##     <name>French Toast</name>
##     <price>$4.50</price>
##     <description>Thick slices made from our homemade sourdough bread</description>
##     <calories>600</calories>
##   </food>
##   <food>
##     <name>Homestyle Breakfast</name>
##     <price>$6.95</price>
##     <description>Two eggs, bacon or sausage, toast, and our ever-popular hash browns</description>
##     <calories>950</calories>
##   </food>
## </breakfast_menu>
## 
```

```r
rootNode <- xmlRoot(doc)
rootNode
```

```
## <breakfast_menu>
##   <food>
##     <name>Belgian Waffles</name>
##     <price>$5.95</price>
##     <description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
##     <calories>650</calories>
##   </food>
##   <food>
##     <name>Strawberry Belgian Waffles</name>
##     <price>$7.95</price>
##     <description>Light Belgian waffles covered with strawberries and whipped cream</description>
##     <calories>900</calories>
##   </food>
##   <food>
##     <name>Berry-Berry Belgian Waffles</name>
##     <price>$8.95</price>
##     <description>Light Belgian waffles covered with an assortment of fresh berries and whipped cream</description>
##     <calories>900</calories>
##   </food>
##   <food>
##     <name>French Toast</name>
##     <price>$4.50</price>
##     <description>Thick slices made from our homemade sourdough bread</description>
##     <calories>600</calories>
##   </food>
##   <food>
##     <name>Homestyle Breakfast</name>
##     <price>$6.95</price>
##     <description>Two eggs, bacon or sausage, toast, and our ever-popular hash browns</description>
##     <calories>950</calories>
##   </food>
## </breakfast_menu>
```

```r
xmlName(rootNode)
```

```
## [1] "breakfast_menu"
```

```r
names(rootNode)
```

```
##   food   food   food   food   food 
## "food" "food" "food" "food" "food"
```

```r
rootNode[[1]]
```

```
## <food>
##   <name>Belgian Waffles</name>
##   <price>$5.95</price>
##   <description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
##   <calories>650</calories>
## </food>
```

```r
rootNode[[1]][[3]]
```

```
## <description>Two of our famous Belgian Waffles with plenty of real maple syrup</description>
```

```r
xmlSApply(rootNode, xmlValue)
```

```
##                                                                                                                     food 
##                               "Belgian Waffles$5.95Two of our famous Belgian Waffles with plenty of real maple syrup650" 
##                                                                                                                     food 
##                    "Strawberry Belgian Waffles$7.95Light Belgian waffles covered with strawberries and whipped cream900" 
##                                                                                                                     food 
## "Berry-Berry Belgian Waffles$8.95Light Belgian waffles covered with an assortment of fresh berries and whipped cream900" 
##                                                                                                                     food 
##                                                "French Toast$4.50Thick slices made from our homemade sourdough bread600" 
##                                                                                                                     food 
##                         "Homestyle Breakfast$6.95Two eggs, bacon or sausage, toast, and our ever-popular hash browns950"
```

```r
xpathSApply(rootNode, "//name", xmlValue)
```

```
## [1] "Belgian Waffles"             "Strawberry Belgian Waffles" 
## [3] "Berry-Berry Belgian Waffles" "French Toast"               
## [5] "Homestyle Breakfast"
```

```r
xpathSApply(rootNode, "//price", xmlValue)
```

```
## [1] "$5.95" "$7.95" "$8.95" "$4.50" "$6.95"
```

```r
xpathSApply(rootNode, "//description", xmlValue)
```

```
## [1] "Two of our famous Belgian Waffles with plenty of real maple syrup"                  
## [2] "Light Belgian waffles covered with strawberries and whipped cream"                  
## [3] "Light Belgian waffles covered with an assortment of fresh berries and whipped cream"
## [4] "Thick slices made from our homemade sourdough bread"                                
## [5] "Two eggs, bacon or sausage, toast, and our ever-popular hash browns"
```

```r
xpathSApply(rootNode, "//calories", xmlValue)
```

```
## [1] "650" "900" "900" "600" "950"
```

```r



## Reading
fileUrl <- "http://espn.go.com/nfl/team/_/name/bal/baltimore-ravens"
doc <- htmlTreeParse(fileUrl, useInternal = TRUE)
scores <- xpathSApply(doc, "//li[@class='score']", xmlValue)
teams <- xpathSApply(doc, "//li[@class='team-name']", xmlValue)
scores
```

```
## list()
```

```r
teams
```

```
##  [1] "San Francisco" "Dallas"        "Washington"    "New Orleans"  
##  [5] "Cincinnati"    "Pittsburgh"    "Cleveland"     "Carolina"     
##  [9] "Indianapolis"  "Tampa Bay"     "Atlanta"       "Cincinnati"   
## [13] "Pittsburgh"    "Tennessee"     "New Orleans"   "San Diego"    
## [17] "Miami"         "Jacksonville"  "Houston"       "Cleveland"
```

```r

```




## Reading JSON


```r

## install.packages('jsonlite')
library(jsonlite)
jsonData <- fromJSON("https://api.github.com/users/jtleek/repos")
names(jsonData)
```

```
##  [1] "id"                "name"              "full_name"        
##  [4] "owner"             "private"           "html_url"         
##  [7] "description"       "fork"              "url"              
## [10] "forks_url"         "keys_url"          "collaborators_url"
## [13] "teams_url"         "hooks_url"         "issue_events_url" 
## [16] "events_url"        "assignees_url"     "branches_url"     
## [19] "tags_url"          "blobs_url"         "git_tags_url"     
## [22] "git_refs_url"      "trees_url"         "statuses_url"     
## [25] "languages_url"     "stargazers_url"    "contributors_url" 
## [28] "subscribers_url"   "subscription_url"  "commits_url"      
## [31] "git_commits_url"   "comments_url"      "issue_comment_url"
## [34] "contents_url"      "compare_url"       "merges_url"       
## [37] "archive_url"       "downloads_url"     "issues_url"       
## [40] "pulls_url"         "milestones_url"    "notifications_url"
## [43] "labels_url"        "releases_url"      "created_at"       
## [46] "updated_at"        "pushed_at"         "git_url"          
## [49] "ssh_url"           "clone_url"         "svn_url"          
## [52] "homepage"          "size"              "stargazers_count" 
## [55] "watchers_count"    "language"          "has_issues"       
## [58] "has_downloads"     "has_wiki"          "forks_count"      
## [61] "mirror_url"        "open_issues_count" "forks"            
## [64] "open_issues"       "watchers"          "default_branch"
```

```r
names(jsonData$owner)
```

```
##  [1] "login"               "id"                  "avatar_url"         
##  [4] "gravatar_id"         "url"                 "html_url"           
##  [7] "followers_url"       "following_url"       "gists_url"          
## [10] "starred_url"         "subscriptions_url"   "organizations_url"  
## [13] "repos_url"           "events_url"          "received_events_url"
## [16] "type"                "site_admin"
```

```r
jsonData$owner$login
```

```
##  [1] "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek"
##  [8] "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek"
## [15] "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek"
## [22] "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek" "jtleek"
## [29] "jtleek" "jtleek"
```

```r

## iris
myjson <- toJSON(iris, pretty = TRUE)
cat(myjson)
```

```
## [
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.7,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.6,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.6,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3.9,
## 		"Petal.Length" : 1.7,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.6,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.4,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.1,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3.7,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.8,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.8,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.1,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.3,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.1,
## 		"Petal.Width" : 0.1,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 4,
## 		"Petal.Length" : 1.2,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 4.4,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3.9,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 1.7,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.7,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.7,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.6,
## 		"Sepal.Width" : 3.6,
## 		"Petal.Length" : 1,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 1.7,
## 		"Petal.Width" : 0.5,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.8,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.9,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.2,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.2,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.7,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.8,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.2,
## 		"Sepal.Width" : 4.1,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.1,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 4.2,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 1.2,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 3.6,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.1,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.4,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.5,
## 		"Sepal.Width" : 2.3,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.4,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 1.3,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.5,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.6,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 1.9,
## 		"Petal.Width" : 0.4,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.8,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.3,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 1.6,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 4.6,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5.3,
## 		"Sepal.Width" : 3.7,
## 		"Petal.Length" : 1.5,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 1.4,
## 		"Petal.Width" : 0.2,
## 		"Species" : "setosa"
## 	},
## 	{
## 		"Sepal.Length" : 7,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 4.7,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.9,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 4.9,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 2.3,
## 		"Petal.Length" : 4,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.5,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.6,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 4.7,
## 		"Petal.Width" : 1.6,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 2.4,
## 		"Petal.Length" : 3.3,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.6,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.6,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.2,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 3.9,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 2,
## 		"Petal.Length" : 3.5,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.9,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.2,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 2.2,
## 		"Petal.Length" : 4,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.7,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 3.6,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 4.4,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 4.1,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.2,
## 		"Sepal.Width" : 2.2,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 3.9,
## 		"Petal.Width" : 1.1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.9,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 4.8,
## 		"Petal.Width" : 1.8,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 4.9,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.7,
## 		"Petal.Width" : 1.2,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.3,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.6,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.4,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.8,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.8,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5,
## 		"Petal.Width" : 1.7,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 2.6,
## 		"Petal.Length" : 3.5,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 2.4,
## 		"Petal.Length" : 3.8,
## 		"Petal.Width" : 1.1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 2.4,
## 		"Petal.Length" : 3.7,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 3.9,
## 		"Petal.Width" : 1.2,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 1.6,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.4,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.6,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 4.7,
## 		"Petal.Width" : 1.5,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.3,
## 		"Petal.Length" : 4.4,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.1,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 4,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.5,
## 		"Sepal.Width" : 2.6,
## 		"Petal.Length" : 4.4,
## 		"Petal.Width" : 1.2,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.6,
## 		"Petal.Width" : 1.4,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.6,
## 		"Petal.Length" : 4,
## 		"Petal.Width" : 1.2,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5,
## 		"Sepal.Width" : 2.3,
## 		"Petal.Length" : 3.3,
## 		"Petal.Width" : 1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 4.2,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.2,
## 		"Petal.Width" : 1.2,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.2,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.2,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 4.3,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.1,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 3,
## 		"Petal.Width" : 1.1,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.1,
## 		"Petal.Width" : 1.3,
## 		"Species" : "versicolor"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 6,
## 		"Petal.Width" : 2.5,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 1.9,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.1,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.9,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.5,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.8,
## 		"Petal.Width" : 2.2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.6,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 6.6,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 4.9,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 4.5,
## 		"Petal.Width" : 1.7,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.3,
## 		"Sepal.Width" : 2.9,
## 		"Petal.Length" : 6.3,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 5.8,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.2,
## 		"Sepal.Width" : 3.6,
## 		"Petal.Length" : 6.1,
## 		"Petal.Width" : 2.5,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.5,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 5.3,
## 		"Petal.Width" : 1.9,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.8,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.5,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.7,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 5,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 2.4,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 5.3,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.5,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.5,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.7,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 6.7,
## 		"Petal.Width" : 2.2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.7,
## 		"Sepal.Width" : 2.6,
## 		"Petal.Length" : 6.9,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 2.2,
## 		"Petal.Length" : 5,
## 		"Petal.Width" : 1.5,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.9,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 5.7,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.6,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.9,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.7,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 6.7,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 4.9,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 5.7,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.2,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 6,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.2,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 4.8,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.9,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.2,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.8,
## 		"Petal.Width" : 1.6,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.4,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 6.1,
## 		"Petal.Width" : 1.9,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.9,
## 		"Sepal.Width" : 3.8,
## 		"Petal.Length" : 6.4,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 2.2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.8,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 1.5,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.1,
## 		"Sepal.Width" : 2.6,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 1.4,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 7.7,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 6.1,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 2.4,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.4,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 5.5,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 4.8,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.9,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 5.4,
## 		"Petal.Width" : 2.1,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 5.6,
## 		"Petal.Width" : 2.4,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.9,
## 		"Sepal.Width" : 3.1,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.8,
## 		"Sepal.Width" : 2.7,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 1.9,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.8,
## 		"Sepal.Width" : 3.2,
## 		"Petal.Length" : 5.9,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3.3,
## 		"Petal.Length" : 5.7,
## 		"Petal.Width" : 2.5,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.7,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.2,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.3,
## 		"Sepal.Width" : 2.5,
## 		"Petal.Length" : 5,
## 		"Petal.Width" : 1.9,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.5,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.2,
## 		"Petal.Width" : 2,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 6.2,
## 		"Sepal.Width" : 3.4,
## 		"Petal.Length" : 5.4,
## 		"Petal.Width" : 2.3,
## 		"Species" : "virginica"
## 	},
## 	{
## 		"Sepal.Length" : 5.9,
## 		"Sepal.Width" : 3,
## 		"Petal.Length" : 5.1,
## 		"Petal.Width" : 1.8,
## 		"Species" : "virginica"
## 	}
## ]
```

```r
iris2 <- fromJSON(myjson)
head(iris2)
```

```
##   Sepal.Length Sepal.Width Petal.Length Petal.Width Species
## 1          5.1         3.5          1.4         0.2  setosa
## 2          4.9         3.0          1.4         0.2  setosa
## 3          4.7         3.2          1.3         0.2  setosa
## 4          4.6         3.1          1.5         0.2  setosa
## 5          5.0         3.6          1.4         0.2  setosa
## 6          5.4         3.9          1.7         0.4  setosa
```



## Using data.table

```r

## install.packages('data.table')
library(data.table)
DF <- data.frame(x = rnorm(9), y = rep(c("a", "b", "c"), each = 3), z = rnorm(9))
head(DF, 3)
```

```
##          x y       z
## 1  0.24441 a  0.4495
## 2 -0.04576 a -1.2629
## 3 -0.47290 a  0.3280
```

```r
DT <- data.table(x = rnorm(9), y = rep(c("a", "b", "c"), each = 3), z = rnorm(9))
head(DT, 3)
```

```
##          x y      z
## 1: -1.9055 a 0.8051
## 2: -1.2414 a 0.6753
## 3:  0.4098 a 1.4035
```

```r
DT[2, ]
```

```
##         x y      z
## 1: -1.241 a 0.6753
```

```r
DT[DT$y == "a", ]
```

```
##          x y      z
## 1: -1.9055 a 0.8051
## 2: -1.2414 a 0.6753
## 3:  0.4098 a 1.4035
```

```r
DT[c(2, 3)]
```

```
##          x y      z
## 1: -1.2414 a 0.6753
## 2:  0.4098 a 1.4035
```

```r
DT[, c(2, 3)]  # not subsetting the columns
```

```
## [1] 2 3
```

```r
{
    x = 1
    y = 2
}
k = {
    print(10)
    5
}  # 10
```

```
## [1] 10
```

```r
print(k)  # 5
```

```
## [1] 5
```

```r
tables()
```

```
##      NAME NROW MB COLS  KEY
## [1,] DT      9 1  x,y,z    
## Total: 1MB
```

```r
DT[, list(mean(x), sum(z))]
```

```
##        V1      V2
## 1: 0.0513 -0.4199
```

```r
DT[, table(y)]
```

```
## y
## a b c 
## 3 3 3
```

```r
DT[, `:=`(w, z^2)]
```

```
##          x y        z        w
## 1: -1.9055 a  0.80505 0.648112
## 2: -1.2414 a  0.67529 0.456021
## 3:  0.4098 a  1.40350 1.969821
## 4:  0.6822 b -1.76135 3.102340
## 5: -0.1438 b  0.51189 0.262027
## 6:  0.4609 b -1.42016 2.016843
## 7: -0.1874 c -0.05003 0.002503
## 8:  2.0230 c  1.07582 1.157381
## 9:  0.3639 c -1.65991 2.755285
```

```r
DT
```

```
##          x y        z        w
## 1: -1.9055 a  0.80505 0.648112
## 2: -1.2414 a  0.67529 0.456021
## 3:  0.4098 a  1.40350 1.969821
## 4:  0.6822 b -1.76135 3.102340
## 5: -0.1438 b  0.51189 0.262027
## 6:  0.4609 b -1.42016 2.016843
## 7: -0.1874 c -0.05003 0.002503
## 8:  2.0230 c  1.07582 1.157381
## 9:  0.3639 c -1.65991 2.755285
```

```r
DT2 <- DT
DT[, `:=`(y, 2)]
```

```
## Warning: Coerced 'double' RHS to 'character' to match the column's type;
## may have truncated precision. Either change the target column to 'double'
## first (by creating a new 'double' vector length 9 (nrows of entire table)
## and assign that; i.e. 'replace' column), or coerce RHS to 'character'
## (e.g. 1L, NA_[real|integer]_, as.*, etc) to make your intent clear and for
## speed. Or, set the column type correctly up front when you create the
## table and stick to it, please.
```

```
##          x y        z        w
## 1: -1.9055 2  0.80505 0.648112
## 2: -1.2414 2  0.67529 0.456021
## 3:  0.4098 2  1.40350 1.969821
## 4:  0.6822 2 -1.76135 3.102340
## 5: -0.1438 2  0.51189 0.262027
## 6:  0.4609 2 -1.42016 2.016843
## 7: -0.1874 2 -0.05003 0.002503
## 8:  2.0230 2  1.07582 1.157381
## 9:  0.3639 2 -1.65991 2.755285
```

```r
DT
```

```
##          x y        z        w
## 1: -1.9055 2  0.80505 0.648112
## 2: -1.2414 2  0.67529 0.456021
## 3:  0.4098 2  1.40350 1.969821
## 4:  0.6822 2 -1.76135 3.102340
## 5: -0.1438 2  0.51189 0.262027
## 6:  0.4609 2 -1.42016 2.016843
## 7: -0.1874 2 -0.05003 0.002503
## 8:  2.0230 2  1.07582 1.157381
## 9:  0.3639 2 -1.65991 2.755285
```

```r
DT2  # it is changed as well
```

```
##          x y        z        w
## 1: -1.9055 2  0.80505 0.648112
## 2: -1.2414 2  0.67529 0.456021
## 3:  0.4098 2  1.40350 1.969821
## 4:  0.6822 2 -1.76135 3.102340
## 5: -0.1438 2  0.51189 0.262027
## 6:  0.4609 2 -1.42016 2.016843
## 7: -0.1874 2 -0.05003 0.002503
## 8:  2.0230 2  1.07582 1.157381
## 9:  0.3639 2 -1.65991 2.755285
```

```r
head(DT, n = 3)
```

```
##          x y      z      w
## 1: -1.9055 2 0.8051 0.6481
## 2: -1.2414 2 0.6753 0.4560
## 3:  0.4098 2 1.4035 1.9698
```

```r
DT[, `:=`(m, {
    tmp <- (x + z)
    log2(tmp + 5)
})]
```

```
##          x y        z        w     m
## 1: -1.9055 2  0.80505 0.648112 1.963
## 2: -1.2414 2  0.67529 0.456021 2.149
## 3:  0.4098 2  1.40350 1.969821 2.768
## 4:  0.6822 2 -1.76135 3.102340 1.971
## 5: -0.1438 2  0.51189 0.262027 2.424
## 6:  0.4609 2 -1.42016 2.016843 2.015
## 7: -0.1874 2 -0.05003 0.002503 2.252
## 8:  2.0230 2  1.07582 1.157381 3.018
## 9:  0.3639 2 -1.65991 2.755285 1.889
```

```r
DT
```

```
##          x y        z        w     m
## 1: -1.9055 2  0.80505 0.648112 1.963
## 2: -1.2414 2  0.67529 0.456021 2.149
## 3:  0.4098 2  1.40350 1.969821 2.768
## 4:  0.6822 2 -1.76135 3.102340 1.971
## 5: -0.1438 2  0.51189 0.262027 2.424
## 6:  0.4609 2 -1.42016 2.016843 2.015
## 7: -0.1874 2 -0.05003 0.002503 2.252
## 8:  2.0230 2  1.07582 1.157381 3.018
## 9:  0.3639 2 -1.65991 2.755285 1.889
```

```r
DT2  # it is changed as well; they point to the same address
```

```
##          x y        z        w     m
## 1: -1.9055 2  0.80505 0.648112 1.963
## 2: -1.2414 2  0.67529 0.456021 2.149
## 3:  0.4098 2  1.40350 1.969821 2.768
## 4:  0.6822 2 -1.76135 3.102340 1.971
## 5: -0.1438 2  0.51189 0.262027 2.424
## 6:  0.4609 2 -1.42016 2.016843 2.015
## 7: -0.1874 2 -0.05003 0.002503 2.252
## 8:  2.0230 2  1.07582 1.157381 3.018
## 9:  0.3639 2 -1.65991 2.755285 1.889
```

```r
DT[, `:=`(a, x > 0)]
```

```
##          x y        z        w     m     a
## 1: -1.9055 2  0.80505 0.648112 1.963 FALSE
## 2: -1.2414 2  0.67529 0.456021 2.149 FALSE
## 3:  0.4098 2  1.40350 1.969821 2.768  TRUE
## 4:  0.6822 2 -1.76135 3.102340 1.971  TRUE
## 5: -0.1438 2  0.51189 0.262027 2.424 FALSE
## 6:  0.4609 2 -1.42016 2.016843 2.015  TRUE
## 7: -0.1874 2 -0.05003 0.002503 2.252 FALSE
## 8:  2.0230 2  1.07582 1.157381 3.018  TRUE
## 9:  0.3639 2 -1.65991 2.755285 1.889  TRUE
```

```r
DT
```

```
##          x y        z        w     m     a
## 1: -1.9055 2  0.80505 0.648112 1.963 FALSE
## 2: -1.2414 2  0.67529 0.456021 2.149 FALSE
## 3:  0.4098 2  1.40350 1.969821 2.768  TRUE
## 4:  0.6822 2 -1.76135 3.102340 1.971  TRUE
## 5: -0.1438 2  0.51189 0.262027 2.424 FALSE
## 6:  0.4609 2 -1.42016 2.016843 2.015  TRUE
## 7: -0.1874 2 -0.05003 0.002503 2.252 FALSE
## 8:  2.0230 2  1.07582 1.157381 3.018  TRUE
## 9:  0.3639 2 -1.65991 2.755285 1.889  TRUE
```

```r
DT[, `:=`(b, mean(x + w)), by = a]
```

```
##          x y        z        w     m     a       b
## 1: -1.9055 2  0.80505 0.648112 1.963 FALSE -0.5274
## 2: -1.2414 2  0.67529 0.456021 2.149 FALSE -0.5274
## 3:  0.4098 2  1.40350 1.969821 2.768  TRUE  2.9883
## 4:  0.6822 2 -1.76135 3.102340 1.971  TRUE  2.9883
## 5: -0.1438 2  0.51189 0.262027 2.424 FALSE -0.5274
## 6:  0.4609 2 -1.42016 2.016843 2.015  TRUE  2.9883
## 7: -0.1874 2 -0.05003 0.002503 2.252 FALSE -0.5274
## 8:  2.0230 2  1.07582 1.157381 3.018  TRUE  2.9883
## 9:  0.3639 2 -1.65991 2.755285 1.889  TRUE  2.9883
```

```r
DT
```

```
##          x y        z        w     m     a       b
## 1: -1.9055 2  0.80505 0.648112 1.963 FALSE -0.5274
## 2: -1.2414 2  0.67529 0.456021 2.149 FALSE -0.5274
## 3:  0.4098 2  1.40350 1.969821 2.768  TRUE  2.9883
## 4:  0.6822 2 -1.76135 3.102340 1.971  TRUE  2.9883
## 5: -0.1438 2  0.51189 0.262027 2.424 FALSE -0.5274
## 6:  0.4609 2 -1.42016 2.016843 2.015  TRUE  2.9883
## 7: -0.1874 2 -0.05003 0.002503 2.252 FALSE -0.5274
## 8:  2.0230 2  1.07582 1.157381 3.018  TRUE  2.9883
## 9:  0.3639 2 -1.65991 2.755285 1.889  TRUE  2.9883
```

```r
set.seed(123)
DT <- data.table(x = sample(letters[1:3], 1e+05, TRUE))
DT[, .N, by = x]
```

```
##    x     N
## 1: a 33387
## 2: c 33201
## 3: b 33412
```

```r
# keys
DT <- data.table(x = rep(c("a", "b", "c"), each = 100), y = rnorm(300))
setkey(DT, x)
DT["a"]
```

```
##      x        y
##   1: a  0.25959
##   2: a  0.91751
##   3: a -0.72232
##   4: a -0.80828
##   5: a -0.14135
##   6: a  2.25701
##   7: a -2.37955
##   8: a -0.45425
##   9: a -0.06007
##  10: a  0.86090
##  11: a -1.78466
##  12: a -0.13074
##  13: a -0.36984
##  14: a -0.18066
##  15: a -1.04973
##  16: a  0.37832
##  17: a -1.37079
##  18: a -0.31612
##  19: a  0.39435
##  20: a -1.68988
##  21: a -1.46234
##  22: a  2.55838
##  23: a  0.08789
##  24: a  1.73141
##  25: a  1.21513
##  26: a  0.29954
##  27: a -0.17246
##  28: a  1.13250
##  29: a  0.02320
##  30: a  1.33587
##  31: a -1.09879
##  32: a -0.58176
##  33: a  0.03892
##  34: a  1.07315
##  35: a  1.34970
##  36: a  1.19528
##  37: a -0.02218
##  38: a  0.69849
##  39: a  0.67241
##  40: a -0.79165
##  41: a -0.21791
##  42: a  0.02307
##  43: a  0.11539
##  44: a -0.27708
##  45: a  0.03688
##  46: a  0.47520
##  47: a  1.70749
##  48: a  1.07601
##  49: a -1.34571
##  50: a -1.44025
##  51: a -0.39393
##  52: a  0.58106
##  53: a -0.17079
##  54: a -0.90585
##  55: a  0.15621
##  56: a -0.37323
##  57: a -0.34587
##  58: a -0.35829
##  59: a -0.13307
##  60: a -0.08960
##  61: a  0.62793
##  62: a -1.42883
##  63: a  0.17255
##  64: a -0.79115
##  65: a  1.26204
##  66: a -0.26941
##  67: a  0.15698
##  68: a -0.76060
##  69: a  1.37060
##  70: a  0.03758
##  71: a  0.44949
##  72: a  2.78869
##  73: a -0.46849
##  74: a  1.01261
##  75: a -0.04374
##  76: a  1.40670
##  77: a  0.41993
##  78: a  0.31009
##  79: a  1.11905
##  80: a -1.29814
##  81: a -1.28248
##  82: a  1.65943
##  83: a  0.78375
##  84: a  0.57771
##  85: a -0.26725
##  86: a -0.64569
##  87: a -0.44953
##  88: a -0.82620
##  89: a  1.05504
##  90: a -0.87927
##  91: a -1.27713
##  92: a -0.63412
##  93: a  0.66470
##  94: a -0.50958
##  95: a  0.40736
##  96: a  1.67775
##  97: a -1.05206
##  98: a -0.63691
##  99: a  0.56539
## 100: a  0.38016
##      x        y
```

```r
# use keys to do joins
DT1 <- data.table(x = c("a", "a", "b", "dt1"), y = 1:4)
DT2 <- data.table(x = c("a", "b", "dt2"), z = 5:7)
setkey(DT1, x)
setkey(DT2, x)
merge(DT1, DT2)
```

```
##    x y z
## 1: a 1 5
## 2: a 2 5
## 3: b 3 6
```

```r
# use keys to fast reading
big_df <- data.frame(x = rnorm(1e+06), y = rnorm(1e+06))
file <- tempfile()
write.table(big_df, file = file, row.names = FALSE, col.names = TRUE, sep = "\t", 
    quote = FALSE)
system.time(fread(file))
```

```
##    user  system elapsed 
##   0.552   0.004   0.555
```

```r
system.time(read.table(file, header = TRUE, sep = "\t"))  # so slow
```

```
##    user  system elapsed 
##  10.704   2.304  13.016
```


## Back wd

```r
setwd(oldwd)
```



