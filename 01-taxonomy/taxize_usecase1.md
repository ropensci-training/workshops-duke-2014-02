## Cleaning taxonomic names




### Load libraries


```r
library(taxize)
```


Most of us will start out with a species list, something like the one below. Note that each of the names is spelled incorrectly.


```r
splist <- c("Helanthus annuus", "Pinos contorta", "Collomia grandiflorra", "Abies magnificaa", 
    "Rosa california", "Datura wrighti", "Mimulus bicolour", "Nicotiana glauca", 
    "Maddia sativa", "Bartlettia scapposa")
```


There are many ways to resolve taxonomic names in taxize. Of course, the ideal name resolver will do the work behind the scenes for you so that you don't have to do things like fuzzy matching. There are a few services in taxize like this we can choose from: One is the Taxonomic Name Resolution Service from iPlant (see function *tnrs*).


```r
# The tnrs function accepts a vector of 1 or more
splist_tnrs <- tnrs(query = splist, getpost = "POST", source = "iPlant_TNRS")

# Remove some fields
(splist_tnrs <- splist_tnrs[, !names(splist_tnrs) %in% c("matchedname", "annotations", 
    "uri")])
```

```
           submittedname         acceptedname    sourceid score
3       Helanthus annuus    Helianthus annuus iPlant_TNRS  0.98
1         Pinos contorta       Pinus contorta iPlant_TNRS  0.96
4  Collomia grandiflorra Collomia grandiflora iPlant_TNRS  0.99
5       Abies magnificaa      Abies magnifica iPlant_TNRS  0.98
10       Rosa california     Rosa californica iPlant_TNRS  0.99
9         Datura wrighti      Datura wrightii iPlant_TNRS  0.98
7       Mimulus bicolour      Mimulus bicolor iPlant_TNRS  0.98
8       Nicotiana glauca     Nicotiana glauca iPlant_TNRS     1
6          Maddia sativa         Madia sativa iPlant_TNRS  0.97
2    Bartlettia scapposa   Bartlettia scaposa iPlant_TNRS  0.98
```

```r

# Note the scores. They suggest that there were no perfect matches, but they
# were all very close, ranging from 0.77 to 0.99 (1 is the highest).  Let's
# assume the names in the 'acceptedName' column are correct (and they should
# be).

# So here's our updated species list
(splist <- as.character(splist_tnrs$acceptedname))
```

```
 [1] "Helianthus annuus"    "Pinus contorta"       "Collomia grandiflora"
 [4] "Abies magnifica"      "Rosa californica"     "Datura wrightii"     
 [7] "Mimulus bicolor"      "Nicotiana glauca"     "Madia sativa"        
[10] "Bartlettia scaposa"  
```



We can also make a tree from our cleaned list of species.  This doesn't work for all taxa, and is based on higher level taxanomic relationships, so polytomy's could be a result.


```r
tree <- phylomatic_tree(taxa = splist, storedtree = "R20120829")
plot(tree)
```

![plot of chunk unnamed-chunk-1](figure/unnamed-chunk-1.png) 


Another option is the Global Names Resolver service from EOL (see function *gnr_resolve*) and 


```r
splist <- c("Pinos contorta", "Collomia grandiflorra", "Abies magnificaa", "Datura wrighti", 
    "Mimulus bicolour", "Nicotiana glauca", "Maddia sativa", "Bartlettia scapposa")

sources <- gnr_datasources()
eol <- sources$id[sources$title == "EOL"]
out <- gnr_resolve(splist, data_source_ids = eol, stripauthority = TRUE)
unique(out)
```

```
          submitted_name data_source_title score        matched_name2
9       Abies magnificaa               EOL 0.750      Abies magnifica
16   Bartlettia scapposa               EOL 0.750   Bartlettia scaposa
8  Collomia grandiflorra               EOL 0.750 Callisia grandiflora
10        Datura wrighti               EOL 0.750      Datura wrightii
13         Maddia sativa               EOL 0.750         Madia sativa
11      Mimulus bicolour               EOL 0.750      Mimulus bicolor
12      Nicotiana glauca               EOL 0.988     Nicotiana glauca
1         Pinos contorta               EOL 0.750       Pinus contorta
```


Finally maybe you're interested in synonyms.  There's function that can grab those for either scientific name or ITIS taxonomic ID.


```r

### We can also get synonyms

# via itis serial number
synonyms(get_tsn("Poa annua"))
```

```
[[1]]
                          name    tsn
1      Poa annua var. aquatica 538978
2       Poa annua var. reptans 538979
3                  Aira pumila 785854
4             Catabrosa pumila 787993
5               Ochlopoa annua 791574
6               Poa aestivalis 793946
7                   Poa algida 793954
8         Poa annua var. annua 802116
9     Poa annua var. eriolepis 802117
10 Poa annua var. rigidiuscula 802119
11        Poa annua f. reptans 803667
```

```r

# Or scientific name
synonyms(c("Poa annua", "Pinus contorta", "Puma concolor"), db = "itis")
```

```
$`Poa annua`
                          name    tsn
1      Poa annua var. aquatica 538978
2       Poa annua var. reptans 538979
3                  Aira pumila 785854
4             Catabrosa pumila 787993
5               Ochlopoa annua 791574
6               Poa aestivalis 793946
7                   Poa algida 793954
8         Poa annua var. annua 802116
9     Poa annua var. eriolepis 802117
10 Poa annua var. rigidiuscula 802119
11        Poa annua f. reptans 803667

$`Pinus contorta`
     name    tsn
1 nomatch 183327

$`Puma concolor`
            name    tsn
1 Felis concolor 180587
```


