
# Analyses reported in the paper

## Maximum-likelihood trees

These trees were used for the TemPest regression of sequence sampling dates against root-to-tip genetic distances (Fig 2c, Extended Data Fig 2, 3). 

- `ZIKV.ZiBRA.ML.tree`
- `ZIKV.ZiBRA.withMalaysia.ML.tree` (with Malaysia 1966)

Maximum-likelihood tree computed in PhyML with bootstrap supports from 100 bootstrap samples:
- `ZIKV.ZiBRA.bootstrap_100.tree`

## HyPhy analyses

- `AM.nexus`: Nexus file with American clade and ML tree.
- `PreAM.nexus`: Nexus file with pre-American clade and ML tree.

## BEAST analyses
All analyses were performed in BEAST v1.8.3 except for BASTA analyses which were performed in BEAST2 v2.4.2.

- Strict clock with Bayesian skyline treeprior: 
	- `ZIKV.ZiBRA.Strict-Skyline.xml` 
	- `ZIKV.ZiBRA.Strict-Skyline.1500.trees.xml` (Empirical tree distribution of 1,500 trees from the posterior)
- Uncorrelated lognormal relaxed clock with Bayesian skyline treeprior: 
	- `ZIKV.ZiBRA.UCLN-Skyline.xml` 
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.trees.xml` (Empirical tree distribution of 1,500 trees from the posterior)
- Evolutionary rates of different genes (Extended Data Table 3a):
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.per_gene_rates.xml`
- Phylogeography with asymmetric DTA (Fig 3, 4 Extended Data Table 3c):
	- `ZIKV.ZiBRA.UCLN-Skyline.1500.completehistory_asymRegion.xml`
	- `Figure3.tre` (MCC tree)
	- `Figure3withSEAsia.tre` (MCC tree including sequences from Southeast Asia)


### Model selection 
Used for Path-sampling and Stepping stone analyses to select best fitting coalescent and clock models (Extended Data Table 3a).

- Strict clock
	- `ZIKV.ZiBRA.Strict-Const.xml` (Constant coalescent)
	- `ZIKV.ZiBRA.Strict-Expo.xml` (Exponential growth coalescent)
	- `ZIKV.ZiBRA.Strict-Skyline.xml` (Bayesian Skyline)
- Uncorrelated lognormal relaxed clock
	- `ZIKV.ZiBRA.UCLN-Const.xml` (Constant coalescent)
	- `ZIKV.ZiBRA.UCLN-Expo.xml` (Exponential growth coalescent)
	- `ZIKV.ZiBRA.UCLN-Skyline.xml` (Bayesian Skyline)

### Phylogeography 
Using complete dataset and 10 jackknife resampled datasets with 74 sequences each (10 per location) used to assess robustness of ancestral node locations inferred in the phylogeography analysis (Fig 3, 4, Extended Data Fig 4, Extended Data Table 3c). 

- Asymmetric DTA (strict clock)
	- `DTA_Strict_Skyline/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.Strict-Skyline.1500.completehistory_asymRegion.xml` (Compelte 254 sequence dataset)
	- `DTA_Strict_Skyline/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.Strict-Skyline.1500.completehistory_asymRegion.region.MCC` (MCC tree for the complete dataset)
	- `DTA_Strict_Skyline/Random_subsampling/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.Strict-Skyline.1500.completehistory_asymRegion.subXXX.n10.xml` (10 resampled datasets)
	- `DTA_Strict_Skyline/Random_subsampling/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.Strict-Skyline.1500.completehistory_asymRegion.region.subXXX.n10.MCC.tree` (MCC trees for resampled datasets)
- Asymmetric DTA (uncorrelated lognormal relaxed clock)
	- `DTA_UCLN_Skyline/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.UCLN-Skyline.1500.completehistory_asymRegion.xml` (Compelte 254 sequence dataset)
	- `DTA_UCLN_Skyline/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.UCLN-Skyline.1500.completehistory_asymRegion.region.MCC` (MCC tree for the complete dataset)
	- `DTA_UCLN_Skyline/Random_subsampling/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.UCLN-Skyline.1500.completehistory_asymRegion.subXXX.n10.xml` (10 resampled datasets)
	- `DTA_UCLN_Skyline/Random_subsampling/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.UCLN-Skyline.1500.completehistory_asymRegion.region.subXXX.n10.MCC.tree` (MCC trees for resampled datasets)
- BASTA
	- `BASTA/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.basta.xml` (Complete 254 sequence dataset)
	- `BASTA/Random_subsampling/ZIKV.ZiBRA_no3Rio-Pardis_noFlorida-4_Mexico_Chiu.allGenBank.basta.subXXX.n10.xml` (10 resampled datasets)


### Note
All analyses using the empirical tree distributions (all phylogeography and per-gene rates of evolution) will need to have the line referring to the empirical tree distribution modified before it will run in BEAST:

```XML
<!-- Defining empirical tree distribution -->
<empiricalTreeDistributionModel id="treeModel" fileName="EmpiricalTreeDistribution.trees">
	<taxa idref="taxa"/>
</empiricalTreeDistributionModel>
```
