# Scholarly Paper Recommendation

The project is about recommending relevant scholarly papers to researchers based on their research interests which can be inferred from their published papers. We used a pretrained word2vec model to get feature vectors of user's profile and candidate paper to recommend


## Dataset description
The project use the [dataset 2](https://scholarbank.nus.edu.sg/handle/10635/146027) released by Kazunari Sugiyama and Min-Yen Kan in National University of Singapore. We appreciated the creator of the dataset for sharing the raw pdf files .

**Raw dataset including:**

* Research interests of 50 researchers
	* Each researcher's published papers in DBLP list (full text in pdf format)
	* Paper IDs relevant to each researcher's interests
* Candidate papers to recommend: 95,238 (full text in pdf format)



## Prerequisites

Python packages: pdfminer.six

## Experiment pipeline

**Pipeline**

1. Data preprocessing
	* convert all papers (researchers's published papers and candidate papers to recommend) from pdf format to plain text format (pdf2text.py)
	* text cleaning
	* use all cleaned candidate papers to generate a corpus for word2vec model training
2. Pretraining a  word2vec model based on the corpus of all candidate papers to recommend

## Contributior
* **Name**
* **Name**
## Authors

* **Xueli Pan** 

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Acknowledgments

* Hat tip to anyone whose code was used

