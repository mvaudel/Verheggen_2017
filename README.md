# Verheggen _et al._ 2017

This repository provides additional information to the review entitled _Anatomy and evolution of database search engines-a central component of mass spectrometry based proteomic workflows_ by Verheggen _et al._ ([link](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/manuscript/Verheggen_et_al-2017-Mass_Spectrometry_Reviews.pdf), [pubmed](https://www.ncbi.nlm.nih.gov/pubmed/28902424)).


## Figure 3

Figure 3 is an attempt at showing search engine adoption trends by tracking the number of citations. Citations are manually extracted from Thomson Reuters™ Web of Science™ for the search engines from Table 1, the ten search engines with the most overall number of citations are plotted individually and the others groupped. The data used to generate the original figure are available [here](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/citations/Supplementary%20Material%20-%20data.xlsx).

Below is an update of this Figure made on the 26 Feb. 2019. The data are available [here](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/citations/Supplementary%20Material%20-%20data.xlsx). The script used to generate the figure is available [here](https://github.com/mvaudel/Verheggen_2017/blob/master/R/cumulative_citation_figure.R).

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/cumulative.png)

As expressed in the manuscript, this figure was made to get an idea of the respective adoption levels of search engines by the community but should be used with caution. Notably, citations are a poor indicator of non-academic use, and use of non-academic software. They do not provide any information on the scientific quality or reliability of the different search engines. Also, note that the citations for most recent years might not be indexed to the same level as the earlier years.

As noted in the original manuscript, _the increasing prevalence of other algorithms (a category that includes recent engines such asMS
Amanda and MS-GF+) shows the interest of the community for more innovative approaches_. Sorting the search engines based on the total number of citations penalizes these recent engines. The figure below shows the rank of search engine number of citations when using only the years 2017 and 2018, as well as the rank gain compared to a ranking taking into account all citations. For example, MS-GF+ is rank 5 for the years 2017-2018, +5 compared to the rank using all citations (10). The script used to generate the figure is available [here](https://github.com/mvaudel/Verheggen_2017/blob/master/R/rank_figure.R).

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/rank_delta.png)


## Figure 4

figure 4 aimed at representing how the search parameters influence the search space. One can find very divering opinions in the literature on the influence of the search parameters on the search space, but little data. Using a simple example, we thus attempted at giving estimates on the actual consequences of relaxing search parameters.

The [example file from our tutorials](https://compomics.com/bioinformatics-for-proteomics/identification/), a 1 hour gradient HeLa measurement on a Q Exactive, was searched with different search settings relaxing one parameter at a time compared to thethe Default search settings, and the effect on the search space and identification yield measured in various ways.


### Search settings

14 different ways of enlarging the search space were benchmarked, as listed in the table below. Search settings are groupped into seven categories: (1) _Database_ for changes in the database, (2) _Digestion_ for changes in the protein digestion settings, (3) _Modifications_ for changes in the variable modifications taken into account, (4) _Fragmentation_ for changes in the fragment ions considered, (5) _Tolerances_ for changes in the m/z tolerances, (6) _Isotopes_ for changes in the isotope correction, and (7) _Charges_ for changes in the precursor charges considered.

|     | Category        | Name            | Description                                                                                             |
| --- |:---------------:|:---------------:| ------------------------------------------------------------------------------------------------------- |
| 0   | Default         | Default         | The default search parameters                                                                           |
| 1   | Database        | Isoforms        | Search with isoforms included                                                                           |
| 2   | Database        | Trembl          | Search with Trembl sequences included                                                                   |
| 3   | Database        | Vertebrates     | Search of all Vertebrate sequences                                                                      |
| 4   | Digestion       | 4 mc            | Search with 4 missed cleavages allowd                                                                   |
| 5   | Digestion       | Semispecific    | Search using semispecific digestion                                                                     |
| 6   | Modifications   | Variable Cmm    | Search with cysteine carbamidomethylation as variable                                                    |
| 7   | Modifications   | Phosphorylation | Search with phosphorylation of S, T, Y as variable modificaiton (up to 5 modification sites tested)     |
| 8   | Fragmentation   | A,B,Y           | Search including a ions                                                                                 |
| 9   | Fragmentation   | A,B,C,X,Y,Z     | Search including all fragment ions                                                                      |
| 10  | Tolerances      | MS2 0.5 Da      | Search with 0.5 Da as MS2 tolerance                                                                     |
| 11  | Tolerances      | MS1&2 0.5 Da    | Search with 0.5 Da as MS1 and MS2 tolerance                                                             |
| 12  | Isotopes        | -4 to +4 Da     | Search including isotope correction from -4 to +4 Da                                                    |
| 13  | Charges         | 1 to 4          | Search including charge 1 to 4                                                                          |
| 14  | Charges         | 1 to 6          | Search including charge 1 to 6                                                                          |


### A- Search space

The density of the number of possible peptides per precursor is plotted as violin plot for every parameter of Table 1 after logarithm base 10 transformation. In each case, a large dash represents the median and two smaller dashes represent the upper and lower quartiles. The densities are colored according to the categories of Table 1 and ordered by increasing median.

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/searchSpace.png)

### B- Zeros

The number of peptides considered during the search is plotted for every setting of Table 1 in the same order and coloring as for Figure 4A. The peptides with a hyperscore > 0 are outlined in black.

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/nZeros.png)


### C- False positive score distribution

The density of the scores of decoy hits are plotted as in Figure 4A using the same order.

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/scores.png)


### D- ID rate

The number of target PSMs in every condition is plotted at 1%, 5%, and 10% FDR in green, orange, and red, respectively.

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/idRate.png)


## A big thank to our reviewers

If you find this manuscript of interest, it is in great part thanks to the very valuable comments of the scientists who took the time to review it. All reviewers contributed to make the text more accurate, clearer, and data-driven. So a big thank to our colleagues who took the time to improve this work.
The work on Figure 4 is notably the result of a suggestion to redo our figure in a data-driven way. Our original version (below) was misleading and, as a reviewer rightfully put it, _awful even for an amateur graphic generated by a researcher using PowerPoint_. We hope that you will agree that the current version is an improvement.

![](https://github.com/mvaudel/Verheggen_2017/blob/master/docs/figures/original.png)

