
# Analyses reported in the paper

## Maximum-likelihood trees

These trees were used for the TemPest regression of sequence sampling dates against root-to-tip genetic distances (Fig 2c, Extended Data Fig 2,3). 

- `ZIKV.ZiBRA.ML.tree`
- `ZIKV.ZiBRA.withMalaysia.ML.tree` (with Malaysia 1966)

## BEAST analyses
All analyses were performed in BEAST v1.8.3 except for BASTA analyses which were performed in BEAST2 v2.4.2.

- Uncorrelated lognormal relaxed clock with Bayesian skyline treeprior: 
	- `ZIKV.ZiBRA.UCLN-Skyline.xml`
- Empirical tree distribution of 1,500 sampled molecular clock trees from the posterior after removing burn-in: 
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.trees`


- Evolutionary rates of different genes (Extended Data Table 3a):
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.per_gene_rates`


- Phylogeography (Fig 3, 4 Extended Data Tables 3b, c):
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.completehistory_asymRegion`
	- `Figure3.tre` (MCC tree)
	- `Figure3withSEAsia.tre` (MCC tree including sequences from Southeast Asia)


### Model selection (Extended Data Table 3a)
Used for Path-sampling and Stepping stone

- Strict clock
	- Constant coalescent
	- Exponential growth coalescent
	- Bayesian Skyline
	- Bayesian Skygrid
- Uncorrelated lognormal relaxed clock
	- Constant coalescent
	- Exponential growth coalescent
	- Bayesian Skyline
	- Bayesian Skygrid


### Phylogeography subsampling (Extended Data Fig 4)
10 jackknife resampled datasets (74 sequences each, with 10 sequences per location)

- Asymmetric DTA
- BASTA


### Note
All analyses using the empirical tree distributions (all phylogeography and per-gene rates of evolution) will need to have the line referring to the empirical tree distribution changed before it will run in BEAST:

```XML
  <!-- Defining empirical tree distribution -->
  <empiricalTreeDistributionModel id="treeModel" fileName="EmpiricalTreeDistribution.trees">
		<taxa idref="taxa"/>
  </empiricalTreeDistributionModel>
```