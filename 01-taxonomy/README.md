# Taxonomy suite at rOpenSci

__taxize__

---

## Install taxize locally

If you want the stable version you can install it directly from [CRAN](cran.r-project.org/)

```coffee
install.packages("taxize")
```

Otherwise if you have the [devtools] library installed, you can get the most up to date version from github.

```coffee
library(devtools)
install_github("taxize","ropensci")
```

You can see more about taxize on the [github repo](http://www.github.com/ropensci/taxize), and read about it in the [F1000 manuscript](http://dx.doi.org/10.12688/f1000research.2-191.v2).

Today we'll cover:

    * How to get a list of [identifiers](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/identifiers.md)
    * Taxanomic name cleaning and scrubbing and plotting basic phylogenies in [use case 1.](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/taxize_usecase1.md)
    * Converting scientific names to [common names](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/taxize_usecase2.md)
    * Getting upstream taxonomies from a [list of species](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/taxize_usecase3.md)
    * Get [downstream names too](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/taxize_usecase5.md)
    * How to aggregate data at different [taxonomic hierarchies.](https://github.com/ropensci/workshops-duke-2014-02/blob/master/01-taxonomy/taxize_usecase4.md)

