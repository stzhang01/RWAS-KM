# Users' Manual of RWAS-KM (Version 1.0)
RWAS-KM: Novel Regulome-Wide Association Study Algorithm to Identify Key Regulatory Elements in Dissecting the Genetic Landscape of Cancer.

## Instructions
RWAS can be divided into two steps: the training step and the prediction step. The core of RWAS is the prediction of the chromatin accessibility using genetic variants, associating these predictions with phenotype. RWAS-KM employs either a linear model or marginal effect analysis for the initial feature selection, guided by the chromatin accessibility signals. This integrated approach promises more accurate and reliable identification of accessibility peaks and functional interpretations, deepening our understanding of the genetic mechanisms underpinning various cancers. Initially, leveraging insights from existing RWAS, we selected and assigned weights to a set of genetic variants. These weights were determined based on their correlation with RWAS peak expressions, utilizing either lasso weights derived from RWAS or marginal effects calculated for each SNP. In the second step, we employed a kernel machine to aggregate these weighted variants, subsequently constructing an association score test.<br><br>
![RWAS-KM](https://github.com/stzhang01/RWAS-KM/blob/main/FIGURE-1.png)<br>

## Installation
RWAS-KM is a batteries-included JAR executable. All needed external jar packages are included in the downloadable, RWAS-KM.jar. To download all necessary files, users can use the command: `git clone https://github.com/stzhang01/RWAS-KM.git`<br>

- **Required software and R packages**
  - PLINK v1.9 (https://www.cog-genomics.org/plink/)
  - R software (https://www.r-project.org/)
  - SKAT >= 2.2.5 (https://cran.r-project.org/web/packages/SKAT/index.html)

- **Usage**
  - If trying csv format, the command line is:
  ```java
  java  -jar  RWAS-KM.jar  RWAS-KM  -format  csv  -input_genotype  path/to/ example.csv  -input_phenotype  path/to/ example.tsv  -input_phenotype_column  2  -input_phenotype_type  binary  -weights_info  path/to/RWAS_top1.txt  -peak ACC_1002  -plink  path/to/plink  -Rscript  path/to/Rscript  -output_folder  path/to/output_folder
    ```
  - If trying plink format, the command line is:
  ```java
  java  -jar  RWAS-KM.jar  RWAS-KM  -format  plink  -input_genotype  path/to/example.tped  -input_phenotype  path/to/example.tfam  -input_phenotype_column  6  -input_phenotype_type  binary  -weights_info  path/to/RWAS_top1.txt  - peak ACC_1002  -plink  path/to/plink  -Rscript  path/to/Rscript  -output_folder  path/to/output_folder
    ```

- **Arguments**
  - **format:** the format of genotype and phenotype data, plink or csv.
  - **input_genotype:** genotype file.
  - **input_phenotype:** phenotype file.
  - **input_phenotype_column:** the column of phenotype in the phenotype file.
  - **input_phenotype_type:** the type of phenotype, continuous or binary.
  - **weights_info:** weights file between SNPs and regulome.
  - **gene:** the name of regulome peak.
  - **plink:** plink command path.
  - **Rscript:** Rscript command path.
  - **output_folder:** path of the output file.

## Citations
Please cite the following manuscript for RWAS weights:<br>
Grishin, D., Gusev, A. Allelic imbalance of chromatin accessibility in cancer identifies candidate causal risk variants and their mechanisms. Nat Genet 54, 837–849 (2022). https://doi.org/10.1038/s41588-022-01075-2<br>
Please cite the following manuscript for RWAS-KM software:<br>

## Contacts
Chen Cao : caochen@njmu.edu.cn<br>
Ning Gu : guning@nju.edu.cn<br>

## Copyright License (MIT Open Source)
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT
NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR
OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE. 
