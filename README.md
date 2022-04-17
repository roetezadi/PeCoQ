# PeCoQ: Persian Complex Question Answering Dataset
PeCoQ is an open-domain Persian complex question answering dataset that contains 10,000 question-answer pairs. The paper can be found [PeCoQ: A Dataset for Persian Complex Question Answering over Knowledge Graph](https://arxiv.org/abs/2106.14167).

The characteristic of PeCoQ is as follow:

- Complexity types in PeCoQ can be divided into 6 categories: Multi-Hop Relation, Aggregation, Superlative, Comparative, Explicit Temporal, and Implicit Temporal. 
- For each question, two paraphrases are written by linguists.
- Entities and Relations are provided as well.

Some samples are provided below:
```json
{
            "MachineGenerated": "نام رهبر شهر دانشگاه_کیوتو چیست؟",
            "Question": [
                "نام شهردار شهری که دانشگاه کیوتو در آن قرار دارد، چیست؟",
                " شهردار شهری که دانشگاه کیوتو در آن قرار دارد، چه نام دارد؟"
            ],
            "QuestionType": "MultiRelationQuestions",
            "Relations": [
                "city",
                "leaderName"
            ],
            "Entities": [
                "دانشگاه کیوتو"
            ],
            "SPARQL": " select distinct ?x where { <http://fkg.iust.ac.ir/resource/دانشگاه_کیوتو> fkgo:city ?o. ?o fkgo:leaderName ?x. }",
            "PreAnswers": [],
            "Answers": [
                "Daisaku_Kadokawa"
            ]
        }
```
```json
{
            "MachineGenerated": "ملیت تاثیر گذاشته آرتور_شوپنهاور که نویسنده کتاب توتم_و_تابو است، چیست؟",
            "Question": [
                "ملیت کسی که از آرتور شوپنهاور تاثیر گرفته و نویسنده کتاب توتم و تابو است، چیست؟",
                "کسی که آرتور شوپنهاور بر او تاثیر گذاشته و کتاب توتم و تابو را تقریر کرده است، چه ملیتی دارد؟"
            ],
            "QuestionType": "MultiRelationQuestions",
            "Relations": [
                "influenced",
                "nationality",
                "author"
            ],
            "Entities": [
                "آرتور شوپنهاور",
                "کتاب توتم و تابو"
            ],
            "SPARQL": " select distinct ?x where { <http://fkg.iust.ac.ir/resource/آرتور_شوپنهاور> <http://fkg.iust.ac.ir/ontology/influenced> ?o. ?o <http://fkg.iust.ac.ir/ontology/nationality> ?x. <http://fkg.iust.ac.ir/resource/توتم_و_تابو> <http://fkg.iust.ac.ir/ontology/author> ?o. }",
            "PreAnswers": [],
            "Answers": [
                "اتریشی"
            ]
        },
```
## Results
We used [A Knowledge-based Approach for Answering Complex Questions in Persian](https://arxiv.org/abs/2107.02040) method to report the first baseline on this dataset. The method we used is based on query graph generation. We see it as a search problem that creates all possible candidate SPARQLs. Then, the best candidate is selected based on Multilingual-BERT. 

- CandidateGeneration:  the results of the whole algorithm without selecting the best match. Just having the correct SPARQL among all generated candidate.
- Total: the results of the whole algorithm + selecting the best match.

<table>
  <tr align='center'>
    <td><b>Method</b></td>
    <td><b>F1-score</b></td>
    <td><b>Precision</b></td>
    <td><b>Recall</b></td>
    <td><b>Accuracy</b></td>
  </tr>
  <tr align='center'>
    <td>CandidateGeneration</td>
    <td>-</td>
    <td>-</td>
    <td>- </td>
    <td>70.72%</td>
  </tr>
  <tr align='center'>
    <td>Total</td>
    <td>62.98%</td>
    <td>71.24%</td>
    <td>56.45%</td>
    <td><b>62.75%</b></td>
  </tr>
</table>

 

## Cite
Please site to us:
```
@inproceedings{etezadi2020pecoq,
  title={PeCoQ: A Dataset for Persian Complex Question Answering over Knowledge Graph},
  author={Etezadi, Romina and Shamsfard, Mehrnoush},
  booktitle={2020 11th International Conference on Information and Knowledge Technology (IKT)},
  pages={102--106},
  year={2020},
  organization={IEEE}
}
```
