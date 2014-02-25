## Aggregate a data set to a taxonomic level




### Load libraries


```r
library(taxize)
library(vegan)
```


### Use the dune dataset from the vegan package


```r
data(dune, package = "vegan")
dune <- dune[, -c(7:30)]  # take a subset
species <- c("Bellis perennis", "Empetrum nigrum", "Juncus bufonius", "Juncus articulatus", 
    "Aira praecox", "Eleocharis parvula")
colnames(dune) <- species
head(dune)
```

```
   Bellis perennis Empetrum nigrum Juncus bufonius Juncus articulatus
2                3               0               0                  0
13               0               0               3                  0
4                2               0               0                  0
16               0               0               0                  3
6                0               0               0                  0
1                0               0               0                  0
   Aira praecox Eleocharis parvula
2             0                  0
13            0                  0
4             0                  0
16            0                  8
6             0                  0
1             0                  0
```


### Aggregate sample to families


```r
agg <- tax_agg(dune, rank = "family", db = "ncbi")
agg
```

```

	Aggregated community data

Level of Aggregation: FAMILY
No. taxa before aggregation: 6
No. taxa after aggregation: 5
No. taxa not found: 0
```


### Extract aggregated community data matrix for further usage

See that data is now aggregated from the original at the species level to the family level


```r
head(dune)
```

```
   Bellis perennis Empetrum nigrum Juncus bufonius Juncus articulatus
2                3               0               0                  0
13               0               0               3                  0
4                2               0               0                  0
16               0               0               0                  3
6                0               0               0                  0
1                0               0               0                  0
   Aira praecox Eleocharis parvula
2             0                  0
13            0                  0
4             0                  0
16            0                  8
6             0                  0
1             0                  0
```

```r
head(agg$x)
```

```
   Asteraceae Cyperaceae Ericaceae Juncaceae Poaceae
2           3          0         0         0       0
13          0          0         0         3       0
4           2          0         0         0       0
16          0          8         0         3       0
6           0          0         0         0       0
1           0          0         0         0       0
```


Check which taxa have been aggregated


```r
agg$by
```

```
            variable        agg
1    Bellis perennis Asteraceae
2    Empetrum nigrum  Ericaceae
3    Juncus bufonius  Juncaceae
4 Juncus articulatus  Juncaceae
5       Aira praecox    Poaceae
6 Eleocharis parvula Cyperaceae
```

