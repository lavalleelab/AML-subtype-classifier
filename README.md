# Transcriptomic classifier for acute myeloid leukemia

Acute myeloid leukemia (AML) is a type of cancer characterized by an overabundance of abnormally differentiated myeloid stem or progenitor cells. Several cytogenetic and mutational abnormalities may explain this phenomenon. However, cases of pediatric AML are generally not due to the same abnormalities as adult cases. It is vital to identify these genetic abnormalities, as they largely define the diagnosis of the disease, and are also intrinsically linked to prognosis and therapy. One way of distinguishing between these different subtypes is through their transcriptomic profile, which can detect aberrantly expressed fusion genes. The use of machine learning in this context is also relevant, as by processing a large number of data, gene expression patterns specific to each subtype can be found and learned to classify AMLs into molecular subgroups.


As a result, we have developed a molecular classifier for AML based on transcriptomic profiles (RNA-seq). AML data come from 5 different cohorts, 3 of them public (TARGET-AML[^1], TCGA-AML[^2], BeatAML[^3]) and 2 local from Quebec (Leucégène[^4] and Signature/Triceps[^5]), which are pediatric or adult. Our total dataset thus comprises 3313 samples, for which we had quantification of their gene expression (in TPM) as well as clinical information enabling us to establish their AML subtype. The classifier takes into account 17 AML subtypes (described in the tutorial). For public data, TPMs were calculated directly from gene-aligned read counts obtained with STAR (with GRCh38 v36). Local data were processed with Trimmomatic (v0.39), STAR (v2.7.11b) and RSEM (v1.3.3). The reference genome for STAR and RSEM is GRCh38 v32. Around 85% of the data were used to train and validate different classification algorithms (K-nearest neighbors, Random Forest, Support Vector Machine, XGBoost, ANN). Our choice of classifier was the best-performing algorithm, which is the Support Vector Machine (SVM) when based on coding genes, excluding those on sexual chromosomes (19,003 genes). The remaining 15% of the data was then used for final testing of the classifier. The final F1 score is 0.799. The classifier is particularly effective for AML subtypes defined by mutually exclusive genetic abnormalities, such as the fusion genes *PML-RARA*, *RUNX1-RUNX1T1*, *CBFB-MYH11*, *DEK-NUP214*, translocations of *KMT2A* and mutations of *NPM1*. Thus, the classifier is an AML diagnostic aid for clinicians.


### Tutorial

- [Python tutorial]


### Authors / Credits

- [Maylis Heussner](https://github.com/maheuss)
- [Véronique Lisi](https://github.com/veroniquelisichusj)
- [Banafsheh Khakipoor](https://github.com/BanafshehKhaki)
- [Sébastien Lemieux](https://github.com/sebastien-lemieux)
- Vincent-Philippe Lavallée

  
  [^1]: Bolouri, H., Farrar, J., Triche, T. and al. The molecular landscape of pediatric acute myeloid leukemia reveals recurrent structural alterations and age-specific mutational interactions. *Nat Med* **24**, 103–112 (2018). https://doi.org/10.1038/nm.4439 
  [^2]: Ley TJ, Miller C, Ding L, Raphael BJ, Mungall AJ, Robertson A, and al. Genomic and epigenomic landscapes of adult de novo acute myeloid leukemia. *N Engl J Med* **368**, 2059-2074 (2013).https://doi.org/10.1056/NEJmoa1301689 
  [^3]: Tyner, J.W., Tognon, C.E., Bottomly, D. and al. Functional genomic landscape of acute myeloid leukaemia. *Nature* **562**, 526–531 (2018). https://doi.org/10.1038/s41586-018-0623-z
  [^4]: https://leucegene.ca/
  [^5]: https://www.inesss.qc.ca/fileadmin/doc/INESSS/Rapports/Biologie_medicale/INESSS_Panels_cancers_pediatriques_SNG_EC.pdf
