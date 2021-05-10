# Netie
An R package to infer the anti-tumor selection pressure for tumors.
## Introduction
The Bayesian Hierarchical Model named Neoantgien-T cell interaction estimation (Netie) is to investigate the neoantigens observed in the patient tumors to esti- mate the history of the immune pressure on the evolution of the tumor clones. The estimation results will answer whether the host immune system has been conferring strong or weaker selection pressure on the tumor clones over the time of tumor development. This may give us a peak into the future of how the mutations and clones will evolve for that patient. The model is based on pyclone estimation results. Essentially, each clone is modelled separately, but sharing some random variables.
![preview](https://github.com/tianshilu/Netie/blob/main/flowchart.jpg) 
Please refer to our lab's website for more information https://qbrc.swmed.edu/labs/wanglab/software.php.
## Installation of the package:
  To install our package, you may simply execute the following codes. 
  ```install.packages('netie')```
  Or
  ```# install.packages("devtools") ```
  ```devtools::install_github("tianshilu/Netie", subdir = "Netie") # don't forget to specify subdir!```
## Dependencies
PyClone; R(version>3.4)
## Guided Tutorial
Command: 
```
netie(input_data,sigma_square = 100000 ,
                                   alpha = 10,beta = 2,sigma_p_sqr = 0.1,sigma_a_sqr = NULL,max_iter =100000,multi_sample = T)
```
* input_data: a list with each data frame as the data for each patient. Each data frame consists 7 columns and each row is for one mutation. The 7 columns are mutation ID, sample ID, cluster ID, cellular prevalence, variant allele prevalence, variant allele frequency, and neoantigen load with column names as "mutation_id","sample_id","cluster_id","cellular_prevalence","variant_allele_frequency", and "neoantigen_load". Please use PyClone or other softwares (https://github.com/tianshilu/Phylogenetic-Tree) to get information of cluster id and cellular prevalence. Please use QBRC mutation calling pipeline (https://github.com/tianshilu/QBRC-Somatic-Pipeline) to call mutations for whole exome sequenicng; QBRC neoantigen calling pipeline (https://github.com/tianshilu/QBRC-Neoantigen-Pipeline) to call neoantigens for whole exome sequencing and RNA sequencing.
* sigma_square, alpha, beta, sigma_p_sqr, sigma_a_sqr: hyperparameters for prior distributions. Please refer to the paper for more details.
* max_iter: the iterations of Markov chain Monte Carlo. 
* multi_sample: use True if one patient has more than one sample.

## Output 
The output is a list with the information of the anti-tumor selection pressure for each clone ac and for the whole tumor a.
