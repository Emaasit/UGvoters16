UGvoters16
==========

What is this?
-------------

**UGvoters16** is a package for the counts of Ugandan registered voters for the 2016 presidential election provided by the [Electoral Commision](http://www.ec.or.ug/) (EC) of Uganda. This package contains the number of registered voters by polling station. This "controversial" data was claimed to contain atleast 20,000 "ghost voters" by members of the Ugandan media because the total count from the each polling station are not equal to the totals reported by the Electoral Commission.

How to use it
-------------

Before you can use the data in R, you need to download it from Github using the following commands:

``` r
installed.packages("devtools")
```

    ##      Package LibPath Version Priority Depends Imports LinkingTo Suggests
    ##      Enhances License License_is_FOSS License_restricts_use OS_type Archs
    ##      MD5sum NeedsCompilation Built

``` r
devtools::install_git("git://github.com/emaasit/UGvoters16.git", branch = "master")
library(UGvoters16)
```

After loading the library, you can create a local data frame using the following command:

``` r
df1 <- UGvoters16
df2 <- analyzed
head(df1)
```

    ##   SER_NO DIST_CODE DISTRICT_NAME EA_CODE       EA_NAME SCTY_CODE
    ## 1      1        01          APAC     002 KWANIA COUNTY        01
    ## 2      2        01          APAC     002 KWANIA COUNTY        01
    ## 3      3        01          APAC     002 KWANIA COUNTY        01
    ## 4      4        01          APAC     002 KWANIA COUNTY        01
    ## 5      5        01          APAC     002 KWANIA COUNTY        01
    ## 6      6        01          APAC     002 KWANIA COUNTY        01
    ##   SCOUNTY_NAME PAR_CODE PARISH_NAME PS_CODE             PS_NAME
    ## 1        ADUKU       01      ADYEDA      01       ADYEDA CENTRE
    ## 2        ADUKU       01      ADYEDA      02 APORWEGI P.7 SCHOOL
    ## 3        ADUKU       01      ADYEDA      03        ADYEDA IMALO
    ## 4        ADUKU       02       ALIRA      01             ALIRA B
    ## 5        ADUKU       02       ALIRA      02             AKOT  A
    ## 6        ADUKU       02       ALIRA      03               OLEKE
    ##   NO_OF_FEMALES NO_OF_MALES EC_VOTER_COUNTS ANALYZED_VOTER_COUNT
    ## 1           134         143             277                  277
    ## 2           379         323             703                  702
    ## 3           164         157             322                  321
    ## 4           461         411             872                  872
    ## 5           386         364             750                  750
    ## 6           443         383             826                  826

``` r
head(df2)
```

    ##   SER_NO DIST_CODE DISTRICT_NAME EA_CODE       EA_NAME SCTY_CODE
    ## 1      1         1          APAC       2 KWANIA COUNTY         1
    ## 2      2         1          APAC       2 KWANIA COUNTY         1
    ## 3      3         1          APAC       2 KWANIA COUNTY         1
    ## 4      4         1          APAC       2 KWANIA COUNTY         1
    ## 5      5         1          APAC       2 KWANIA COUNTY         1
    ## 6      6         1          APAC       2 KWANIA COUNTY         1
    ##   SCOUNTY_NAME PAR_CODE PARISH_NAME PS_CODE             PS_NAME
    ## 1        ADUKU        1      ADYEDA       1       ADYEDA CENTRE
    ## 2        ADUKU        1      ADYEDA       2 APORWEGI P.7 SCHOOL
    ## 3        ADUKU        1      ADYEDA       3        ADYEDA IMALO
    ## 4        ADUKU        2       ALIRA       1             ALIRA B
    ## 5        ADUKU        2       ALIRA       2             AKOT  A
    ## 6        ADUKU        2       ALIRA       3               OLEKE
    ##   NO_OF_FEMALES NO_OF_MALES EC_VOTER_COUNTS ANALYZED_VOTER_COUNT
    ## 1            43          51             240                  277
    ## 2           312         251             687                  702
    ## 3            76          66             287                  321
    ## 4           404         349             869                  872
    ## 5           320         296             739                  750
    ## 6           384         317             819                  826

What can you do with it?
------------------------

You can explore for yourself and see why the Ugandan media claimed it has atleast 20,000 "ghost voters".

Example Analysis
----------------

### How many voters are registered

``` r
# what are the column names
names(df1)
```

    ##  [1] "SER_NO"               "DIST_CODE"            "DISTRICT_NAME"       
    ##  [4] "EA_CODE"              "EA_NAME"              "SCTY_CODE"           
    ##  [7] "SCOUNTY_NAME"         "PAR_CODE"             "PARISH_NAME"         
    ## [10] "PS_CODE"              "PS_NAME"              "NO_OF_FEMALES"       
    ## [13] "NO_OF_MALES"          "EC_VOTER_COUNTS"      "ANALYZED_VOTER_COUNT"

``` r
names(df2)
```

    ##  [1] "SER_NO"               "DIST_CODE"            "DISTRICT_NAME"       
    ##  [4] "EA_CODE"              "EA_NAME"              "SCTY_CODE"           
    ##  [7] "SCOUNTY_NAME"         "PAR_CODE"             "PARISH_NAME"         
    ## [10] "PS_CODE"              "PS_NAME"              "NO_OF_FEMALES"       
    ## [13] "NO_OF_MALES"          "EC_VOTER_COUNTS"      "ANALYZED_VOTER_COUNT"

``` r
# count the total number of analyzed voter counts
sum(df2$ANALYZED_VOTER_COUNT)
```

    ## [1] 15277197
