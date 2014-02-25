## Taxonomic hierarchy

A common task is getting the taxonomic tree upstream from your study taxa. We often know what family or order our taxa are in, but it we often don't know the tribes, subclasses, and superfamilies. taxize provides many avenues to getting classifications. Many are accessible via a single function (*classification*), including the Integrated Taxonomic Information System (ITIS) and National Center for Biotechnology Information (NCBI); and via the Catalogue of Life (see function *col_classification*):

Load `taxize`


```r
library(taxize)
```


Define a species list


```r
splist <- c("Rosa californica", "Datura wrightii", "Mimulus bicolor", "Nicotiana glauca", 
    "Madia sativa", "Bartlettia scaposa")
```


Let's get classifications from ITIS using Taxonomic Serial Numbers. Note that we could use uBio instead.


```r
class_list <- classification(splist, db = "itis")
```


And we can combine these all in two different ways


```r
a <- rbind(class_list)
head(a)
```

```
##              names            name          rank
## 1 Rosa californica         Plantae       Kingdom
## 2 Rosa californica  Viridaeplantae    Subkingdom
## 3 Rosa californica    Streptophyta  Infrakingdom
## 4 Rosa californica    Tracheophyta      Division
## 5 Rosa californica Spermatophytina   Subdivision
## 6 Rosa californica    Angiospermae Infradivision
```

```r
tail(a)
```

```
##                 names               name       rank
## 67 Bartlettia scaposa      Magnoliopsida      Class
## 68 Bartlettia scaposa          Asteranae Superorder
## 69 Bartlettia scaposa          Asterales      Order
## 70 Bartlettia scaposa         Asteraceae     Family
## 71 Bartlettia scaposa         Bartlettia      Genus
## 72 Bartlettia scaposa Bartlettia scaposa    Species
```


Or


```r
cbind(class_list)
```

```
##   Kingdom     Subkingdom Infrakingdom     Division     Subdivision
## 1 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
## 2 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
## 3 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
## 4 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
## 5 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
## 6 Plantae Viridaeplantae Streptophyta Tracheophyta Spermatophytina
##   Infradivision         Class Superorder     Order     Family      Genus
## 1  Angiospermae Magnoliopsida    Rosanae   Rosales   Rosaceae       Rosa
## 2  Angiospermae Magnoliopsida  Asteranae Solanales Solanaceae     Datura
## 3  Angiospermae Magnoliopsida  Asteranae  Lamiales Phrymaceae    Mimulus
## 4  Angiospermae Magnoliopsida  Asteranae Solanales Solanaceae  Nicotiana
## 5  Angiospermae Magnoliopsida  Asteranae Asterales Asteraceae      Madia
## 6  Angiospermae Magnoliopsida  Asteranae Asterales Asteraceae Bartlettia
##              Species
## 1   Rosa californica
## 2    Datura wrightii
## 3    Mimulus bicolor
## 4   Nicotiana glauca
## 5       Madia sativa
## 6 Bartlettia scaposa
```

