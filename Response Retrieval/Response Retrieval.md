## Response retrieval
Response retrieval/selection aims to rank/select a proper response from a dialog repository.
Automatic conversation (AC) aims to create an automatic human-computer dialog process for the purpose of question answering, task completion, and social chat (i.e., chit-chat). In general, AC could be formulated either as an IR problem that aims to rank/select a proper response from a dialog repository or a generation problem that aims to generate an appropriate response with respect to the input utterance. Here, we refer response retrieval as the IR-based way to do AC.
Example:
![example](Response Retrieval/example.png)


Dataset
- Ubuntu Dialog Corpus (UDC) contains multi-turn dialogues collected from chat logs of the Ubuntu Forum. The data set consists of 1 million context-response pairs for training, 0.5 million pairs for validation, and 0.5 million pairs for testing. Positive responses are true responses from humans, and negative ones are randomly sampled. The ratio of the positive and the negative is 1:1 in training, and 1:9 in validation and testing. 
- [MSDialog](https://ciir.cs.umass.edu/downloads/msdialog/) is a labeled dialog dataset of question answering (QA) interactions between information seekers and answer providers from an online forum on Microsoft products (Microsoft Community). The dataset contains more than 2,000 multi-turn information-seeking conversations with 10,000 utterances that are annotated with user intent on the utterance level.

- [Douban Conversation Corpus](https://github.com/MarkWuNLP/ MultiTurnResponseSelection) has  1.1 million dyadic dialogues (conversation between two persons) longer than 2 turns from Douban group which is a popular social networking service in China. 0.5 million for training set and 25 thousand dialouges for  validation set, and 1, 000 dialogues for test set.
- [E-commerce Dialogue Corpus](https://github.com/cooelf/DeepUtteranceAggregation)  contains over 5 types of conversations (e.g. commodity consultation, logistics express, recommendation, negotiation and chitchat) based on over 20 commodities. The ratio of the positive and the negative
is 1:1 in training and validation, and 1:9 in testing.

$R_n@k$: recall at position $k$ in $n$ candidates.
<table>
   <tr>
      <td></td>
      <td colspan=5>Ubuntu Corpus</td>
      <td colspan=6>Douban Conversation Corpus</td>
   </tr>
   <tr>
      <td>Model</td>
      <td>MAP</td>
      <td>R2@1</td>
      <td>R10@1</td>
      <td>R10@2</td>
      <td>R10@5</td>
      <td>MAP</td>
      <td>MRR</td>
      <td>P@1</td>
      <td>R10@1</td>
      <td>R10@2</td>
      <td>R10@5</td>
   </tr>
   <tr>
      <td>Multi-View</td>
      <td>\</td>
      <td>0.908</td>
      <td>0.662</td>
      <td>0.801</td>
      <td>0.951</td>
      <td>0.505</td>
      <td>0.543</td>
      <td>0.342</td>
      <td>0.202</td>
      <td>0.35</td>
      <td>0.729</td>
   </tr>
   <tr>
      <td>DL2R</td>
      <td>\</td>
      <td>0.899</td>
      <td>0.626</td>
      <td>0.783</td>
      <td>0.944</td>
      <td>0.488</td>
      <td>0.527</td>
      <td>0.33</td>
      <td>0.193</td>
      <td>0.342</td>
      <td>0.705</td>
   </tr>
   <tr>
      <td>SMN</td>
      <td>0.7327</td>
      <td>0.927</td>
      <td>0.726</td>
      <td>0.847</td>
      <td>0.962</td>
      <td>0.529</td>
      <td>0.572</td>
      <td>0.397</td>
      <td>0.236</td>
      <td>0.396</td>
      <td>0.734</td>
   </tr>
   <tr>
      <td>DAM</td>
      <td>\</td>
      <td>0.938</td>
      <td>0.767</td>
      <td>0.874</td>
      <td>0.969</td>
      <td>0.55</td>
      <td>0.601</td>
      <td>0.427</td>
      <td>0.254</td>
      <td>0.41</td>
      <td>0.757</td>
   </tr>
   <tr>
      <td>DUA</td>
      <td>\</td>
      <td>\</td>
      <td>0.752</td>
      <td>0.868</td>
      <td>0.962</td>
      <td>0.551</td>
      <td>0.599</td>
      <td>0.421</td>
      <td>0.243</td>
      <td>0.421</td>
      <td>0.78</td>
   </tr>
   <tr>
      <td>DMN</td>
      <td>0.7719</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
   </tr>
   <tr>
      <td>U2U-IMN</td>
      <td>0.866</td>
      <td>0.945</td>
      <td>0.79</td>
      <td>0.886</td>
      <td>0.973</td>
      <td>0.564</td>
      <td>0.611</td>
      <td>0.429</td>
      <td>0.259</td>
      <td>0.43</td>
      <td>0.791</td>
   </tr>
   <tr>
      <td>TripleNet</td>
      <td>\</td>
      <td>0.943</td>
      <td>0.79</td>
      <td>0.885</td>
      <td>0.97</td>
      <td>0.564</td>
      <td>0.618</td>
      <td>0.447</td>
      <td>0.268</td>
      <td>0.426</td>
      <td>0.778</td>
   </tr>
   <tr>
      <td>IMN</td>
      <td>\</td>
      <td>0.946</td>
      <td>0.794</td>
      <td>0.889</td>
      <td>0.974</td>
      <td>0.57</td>
      <td>0.615</td>
      <td>0.433</td>
      <td>0.262</td>
      <td>0.452</td>
      <td>0.789</td>
   </tr>
   <tr>
      <td>IoI-local</td>
      <td>\</td>
      <td>0.947</td>
      <td>0.796</td>
      <td>0.894</td>
      <td>0.974</td>
      <td>0.573</td>
      <td>0.621</td>
      <td>0.444</td>
      <td>0.269</td>
      <td>0.451</td>
      <td>0.786</td>
   </tr>
   <tr>
      <td>MSN </td>
      <td>\</td>
      <td>\</td>
      <td>0.8</td>
      <td>0.899</td>
      <td>0.978</td>
      <td>0.587</td>
      <td>0.632</td>
      <td>0.47</td>
      <td>0.295</td>
      <td>0.452</td>
      <td>0.788</td>
   </tr>
   <tr>
      <td>SA-BERT</td>
      <td>\</td>
      <td>0.965</td>
      <td>0.855</td>
      <td>0.928</td>
      <td>0.983</td>
      <td>0.619</td>
      <td>0.659</td>
      <td>0.496</td>
      <td>0.313</td>
      <td>0.481</td>
      <td>0.847</td>
   </tr>
</table>

<table>
   <tr>
      <td></td>
      <td colspan=4>MSDialog</td>
      <td colspan=4>E-commerce Corpus</td>
   </tr>
   <tr>
      <td>Model</td>
      <td>MAP</td>
      <td>Recall@5</td>
      <td>Recall@1</td>
      <td>Recall@2</td>
      <td>MAP</td>
      <td>R10@1</td>
      <td>R10@2</td>
      <td>R10@5</td>
   </tr>
   <tr>
      <td>Multi-View</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.421</td>
      <td>0.601</td>
      <td>0.861</td>
   </tr>
   <tr>
      <td>DL2R</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.399</td>
      <td>0.571</td>
      <td>0.842</td>
   </tr>
   <tr>
      <td>SMN</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.453</td>
      <td>0.654</td>
      <td>0.886</td>
   </tr>
   <tr>
      <td>DAM</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.526</td>
      <td>0.727</td>
      <td>0.933</td>
   </tr>
   <tr>
      <td>DUA</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.501</td>
      <td>0.7</td>
      <td>0.921</td>
   </tr>
   <tr>
      <td>DMN</td>
      <td>0.6792</td>
      <td>0.9356</td>
      <td>0.5021</td>
      <td>0.7122</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
   </tr>
   <tr>
      <td>U2U-IMN</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.759</td>
      <td>0.616</td>
      <td>0.806</td>
      <td>0.966</td>
   </tr>
   <tr>
      <td>TripleNet</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
   </tr>
   <tr>
      <td>IMN</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.621</td>
      <td>0.797</td>
      <td>0.964</td>
   </tr>
   <tr>
      <td>IoI-local</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.563</td>
      <td>0.768</td>
      <td>0.95</td>
   </tr>
   <tr>
      <td>MSN </td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.606</td>
      <td>0.77</td>
      <td>0.937</td>
   </tr>
   <tr>
      <td>SA-BERT</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>\</td>
      <td>0.704</td>
      <td>0.879</td>
      <td>0.985</td>
   </tr>
</table>


| Model   | Paper / Source | Code | type |
|  ----  | ----  |  ----            | ----  | ----  |
| Multi-View | [Multi-view Response Selection for Human-Computer Conversation](https://www.aclweb.org/anthology/D16-1036.pdf) | | multi-turn |
| DL2R |  [Learning to Respond with Deep Neural Networks for Retrieval-Based Human-Computer Conversation System](http://www.ruiyan.me/pubs/SIGIR2016.pdf)| | multi-turn |
| SMN  |  [Sequential Matching Network: A New Architecture for Multi-turn Response Selection in Retrieval-Based Chatbots](https://www.aclweb.org/anthology/P17-1046.pdf) | [Official](https://github.com/MarkWuNLP/ MultiTurnResponseSelection)| Multi-turn|
|DAM | [Multi-Turn Response Selection for Chatbots with Deep Attention Matching Network](https://www.aclweb.org/anthology/P18-1103.pdf) |[Official](https://github.com/baidu/Dialogue/tree/master/DAM) | multi-turn|
|DUA |[Modeling Multi-turn Conversation with Deep Utterance Aggregation](https://arxiv.org/pdf/1806.09102.pdf)|[Official](https://github.com/cooelf/DeepUtteranceAggregation)|multi-turn|
| DMN | [Response Ranking with Deep Matching Networks and External Knowledge in Information-seeking Conversation Systems](https://arxiv.org/pdf/1805.00188.pdf)|[Official](https://github.com/yangliuy/ NeuralResponseRanking) |multi-turn |
|U2U-IMN| [Utterance-to-Utterance Interactive Matching Network for Multi-Turn Response Selection in Retrieval-Based Chatbots](https://arxiv.org/pdf/1911.06940v1.pdf)|[Official](https://github.com/JasonForJoy/U2U-IMN)|multi-turn|
|TripleNet|[TripleNet: Triple Attention Network for Multi-Turn Response Selection in Retrieval-based Chatbots](https://arxiv.org/pdf/1909.10666v2.pdf)|[Official](https://github.com/wtma/TripleNet.)|multi-turn|
|IMN|[Interactive Matching Network for Multi-Turn Response Selection in Retrieval-Based Chatbots](https://arxiv.org/pdf/1901.01824v2.pdf)|[Official](https://github.com/JasonForJoy/IMN)|multi-turn|
|IOI-local|[One Time of Interaction May Not Be Enough: Go Deep with an Interaction-over-Interaction Network for Response Selection in Dialogues](https://www.aclweb.org/anthology/P19-1001.pdf)|[Official](https://github.com/chongyangtao/IOI)|multi-turn|
|MSN|[Multi-hop Selector Network for Multi-turn Response Selection in Retrieval-based Chatbots](https://www.aclweb.org/anthology/D19-1011.pdf)|[Official](https://github.com/chunyuanY/Dialogue)|multi-turn|
|SA-BERT|[Speaker-Aware BERT for Multi-Turn Response Selection in Retrieval-Based Chatbots](https://arxiv.org/pdf/2004.03588v1.pdf)|[Official](https://github.com/JasonForJoy/SA-BERT)|multi-turn|