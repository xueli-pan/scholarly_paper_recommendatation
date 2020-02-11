# Scholarly Paper Recommendation

The project is about recommending relevant scholarly papers to researchers based on their research interests which can be inferred from their published papers. We used a pretrained word2vec model to get feature vectors of user's profile and candidate paper to recommend


## Dataset description
The project use the [dataset 2](https://scholarbank.nus.edu.sg/handle/10635/146027) released by Kazunari Sugiyama and Min-Yen Kan in National University of Singapore. We appreciated the creator of the dataset for sharing the raw pdf files .

**Raw dataset includes:**

* Research interests of 50 researchers
	* Each researcher's published papers in DBLP list (full text in pdf format)
	* Paper IDs relevant to each researcher's interests (ground truth)
* Candidate papers to recommend: 95,238 (full text in pdf format)
 
**Statistics of user profiles:**

|      |   number of publications  | number of relevant papers|
|:-------------: | :-------------: | :-------------: |
| Min            | 2               |8              |
| Max            | 31              |241            |
| Avg            | 10.68           |74.56          |
| Total          | 534	            |3728           |


	




## Prerequisites

Python packages: pdfminer.six

## Experiment pipeline

**Pipeline**

1. Data preprocessing
	* convert all papers (researchers's published papers and candidate papers to recommend) from pdf format to plain text format (pdf2text.py)
	* text cleaning (text_cleaning.py)
	* use all cleaned candidate papers to generate a corpus for word2vec model training
	
2. Pretraining a  word2vec model based on the corpus of all candidate papers to recommend

3. Candidate papers representation ( *i from 1 to 95238* )
	* Using the pretrain word2vec model to create feature vector for each candidate paper ( *FV<sub>pi</sub>* )
	* using a normal word2vec model to create feature vector for each candidate paper ( *FV<sub>ni</sub>* )
	
4. Researchers interest representation ( *n from 1 to 50* )
	* Using pretrain word2vec model
		* Using the most recent publication of a specific researchers as input to get feature vector the researcher's interest ( *FV<sub>pmn</sub>*, )
		* Using researcher's all publications with the same weight as input( *FV<sub>psn</sub>* )
		* Using researcher's all publications with the different weight stategy as input, the more recent the publication is, the more important ( *FV<sub>pdn</sub>* )
		
	* Using normal word2vec model
		* Using the most recent publication of a specific researchers as input to get feature vector the researcher's interest ( *FV<sub>nmn</sub>* )
		* Using researcher's all publications with the same weight as input( *FV<sub>nsn</sub>* )
		* Using researcher's all publications with the different weight stategy as input, the more recent the publication is, the more important ( *FV<sub>ndn</sub>* )
		
5. Calculating similarity between *FV* for different candidate papers and *FV* for different researchers', get most 10 relervant candidate papers for each type of researchers' interest representation

6. Evaluateing similar ranking results by metrics NDCG@10, MRR@10

## Contributior
* **Name**
* **Name**
## Authors

* **Xueli Pan** 

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used

