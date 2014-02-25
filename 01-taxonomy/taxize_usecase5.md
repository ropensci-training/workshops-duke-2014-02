## Get downstream names!!

We can also get downstream names, in this case all species from the genus *Apis*, getting data from the Catalogue of Life


```r
col_downstream(name = "Apis", downto = "Species")
```

```
## $Apis
##   childtaxa_id     childtaxa_name childtaxa_rank
## 1      6971712 Apis andreniformis        Species
## 2      6971713        Apis cerana        Species
## 3      6971714       Apis dorsata        Species
## 4      6971715        Apis florea        Species
## 5      6971716 Apis koschevnikovi        Species
## 6      6845885     Apis mellifera        Species
## 7      6971717   Apis nigrocincta        Species
```


Or get data from ITIS, in this case get genera downstream from _Pinaceae_


```r
itis_downstream(tsns = 18030, downto = "Genus")
```

```
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=18030
## http://www.itis.gov/ITISWebService/services/ITISService/getHierarchyDownFromTSN?tsn=18030
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=18031
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=18033
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=18035
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=183396
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=183405
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=183409
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=183418
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=822529
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=822530
```

```
##      tsn parentname parenttsn   taxonname rankid rankname
## 1  18031   Pinaceae     18030       Abies    180    Genus
## 2  18033   Pinaceae     18030       Picea    180    Genus
## 3  18035   Pinaceae     18030       Pinus    180    Genus
## 4 183396   Pinaceae     18030       Tsuga    180    Genus
## 5 183405   Pinaceae     18030      Cedrus    180    Genus
## 6 183409   Pinaceae     18030       Larix    180    Genus
## 7 183418   Pinaceae     18030 Pseudotsuga    180    Genus
## 8 822529   Pinaceae     18030  Keteleeria    180    Genus
## 9 822530   Pinaceae     18030 Pseudolarix    180    Genus
```


Get families downstream from _Acridoidea_


```r
itis_downstream(tsns = 650497, "Family")
```

```
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=650497
## http://www.itis.gov/ITISWebService/services/ITISService/getHierarchyDownFromTSN?tsn=650497
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=102195
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657479
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657492
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=650502
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657472
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657473
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657474
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657475
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657476
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657477
## http://www.itis.gov/ITISWebService/services/ITISService/getTaxonomicRankNameFromTSN?tsn=657478
```

```
##       tsn parentname parenttsn      taxonname rankid rankname
## 1  102195 Acridoidea    650497      Acrididae    140   Family
## 2  650502 Acridoidea    650497     Romaleidae    140   Family
## 3  657472 Acridoidea    650497    Charilaidae    140   Family
## 4  657473 Acridoidea    650497   Lathiceridae    140   Family
## 5  657474 Acridoidea    650497     Lentulidae    140   Family
## 6  657475 Acridoidea    650497    Lithidiidae    140   Family
## 7  657476 Acridoidea    650497   Ommexechidae    140   Family
## 8  657477 Acridoidea    650497    Pamphagidae    140   Family
## 9  657478 Acridoidea    650497  Pyrgacrididae    140   Family
## 10 657479 Acridoidea    650497    Tristiridae    140   Family
## 11 657492 Acridoidea    650497 Dericorythidae    140   Family
```

