# French Homograph Disambiguation Dataset

This dataset was created as part of the Blizzard Challenge 2023, with the goal of improving French homograph disambiguation for text-to-speech models. Homographs are words with the same spelling, but different meaning or pronunciation depending on their context in a sentence. They are prevalent in French, and incorrect disambiguation can lead to intelligibility issues.

To disambiguate the pronunciation of homographs, we propose a system that relies on part-of-speech (POS) tagging and suffix families identification. For POS extraction, we use the pre-trained POS tagger [qanastek/pos-french-camembert-flair](https://huggingface.co/qanastek/pos-french-camembert-flair).


## Dataset

The file `homograph_disambiguation_dataset.csv` labels the pronunciation for 35 homographs given their POS tag in a sentence.  A total of **4,091 examples** were manually annotated by a French native speaker. Sentences were extracted from French data used to train [FlauBERT](https://github.com/getalp/Flaubert#31-data), a state-of-the-art BERT for French.

| column name | type | description | example |
|:------------|:-----|:------------|:--------|
| sentence_id | int | The unique identifier of the sentence in the dataset | 1188907 |
| homograph | string | The target homograph to disambiguate | adoptions |
| homograph_index | int | The index position of the token corresponding to the target homograph. Tokens can either be words, punctuations or symbols. Indexing starts at 0. | 6 |
| pos | string | The POS tag of the target homograph in the sentence. For additional information regarding POS tags, please refer to the nomenclature provided in the [POS Tagger Documentation](https://huggingface.co/qanastek/pos-french-camembert-flair#new-additional-pos-tags) | NFP |
| sentence | string | The sentence containing the homograph to disambiguate. Each word/punctuation/symbol is separated by a space, making it easier to tokenize the sentence. | Je disais que 80 % des adoptions par les familles françaises sont faites à l ' étranger . |
| homograph_pronunciation | string | The pronunciation of the target homograph in the sentence. Phonemes are separated by spaces. We use IPA symbols, as in this [open-source phonemizer](https://github.com/bootphon/phonemizer) | a d ɔ p s j ɔ̃ |

Below are the statistics for the number of pronunciations per homograph :

| homograph   | pronunciation   |   count |
|:------------|:----------------|--------:|
| actions     | a k s j ɔ̃<br>a k t j ɔ̃       |     136<br>6 |
| adoptions   | a d ɔ p s j ɔ̃<br>a d ɔ p t j ɔ̃   |      49<br>20 |
| affections  | a f ɛ k s j ɔ̃<br>a f ɛ k t j ɔ̃   |      90<br>19 |
| affluent    | a f l y ɑ̃<br>a f l y       |      66<br>21 |
| as          | a s<br>a             |      64<br>48 |
| bus         | b y s<br>b y            |     166<br>99 |
| but         | b y t<br>b y           |      48<br>6 |
| cacher      | k a ʃ ɛ ʁ<br>k a ʃ e       |      86<br>68 |
| collections | k ɔ l ɛ k s j ɔ̃<br>k ɔ l ɛ k t j ɔ̃ |      87<br>21 |
| content     | k ɔ̃ t ɑ̃<br>k ɔ̃ t          |      99<br>15 |
| convient    | k ɔ̃ v j ɛ̃<br>k ɔ̃ v i       |      43<br>1 |
| couvent     | k u v ɑ̃<br>k u v         |      62<br>20 |
| détections  | d e t ɛ k s j ɔ̃<br>d e t ɛ k t j ɔ̃ |      41<br>20 |
| est         | ɛ s t<br>ɛ           |      87<br>40 |
| excellent   | ɛ k s ɛ l ɑ̃<br>ɛ k s ɛ l      |     138<br>21 |
| ferment     | f ɛ ʁ m ɑ̃<br>f ɛ ʁ m       |      86<br>45 |
| fier        | f j ɛ ʁ<br>f j e         |     130<br>37 |
| fils        | f i s<br>f i l           |     103<br>8 |
| intentions  | ɛ̃ t ɑ̃ s j ɔ̃<br>ɛ̃ t ɑ̃ t j ɔ̃     |      66<br>17 |
| minerai     | m i n ə ʁ ɛ<br>m i n ə ʁ e     |      49<br>5 |
| négligent   | n e ɡ l i ʒ ɑ̃<br>n e ɡ l i ʒ   |     114<br>21 |
| options     | ɔ p s j ɔ̃<br>ɔ p t j ɔ̃       |     114<br>20 |
| os          | ɔ s<br>o             |      34<br>18 |
| parent      | p a ʁ ɑ̃<br>p a ʁ         |     142<br>20 |
| plus        | p l y s<br>p l y         |     100<br>27 |
| portions    | p ɔ ʁ s j ɔ̃<br>p ɔ ʁ t j ɔ̃     |      65<br>22 |
| pressent    | p ʁ ɛ s ɑ̃<br>p ʁ ɛ s       |      28<br>14 |
| reporter    | ʁ ə p ɔ ʁ t ɛ ʁ<br>ʁ ə p ɔ ʁ t e |     137<br>37 |
| résident    | ʁ e z i d ɑ̃<br>ʁ e z i d     |     124<br>21 |
| sens        | s ɑ̃ s<br>s ɑ̃           |      91<br>20 |
| somnolent   | s ɔ m n ɔ l ɑ̃<br>s ɔ m n ɔ l    |     108<br>16 |
| supporter   | s y p ɔ ʁ t ɛ ʁ<br>s y p ɔ ʁ t e |     114<br>36 |
| urgent      | y ʁ ʒ ɑ̃<br>y ʁ ʒ         |     127<br>18 |
| violent     | v j ɔ l ɑ̃<br>v j ɔ l       |      84<br>21 |
| vis         | v i s<br>v i           |     128<br>37 |


## Contributing

Any contribution to this repository is more than welcome.  
If you have any feedback, please send it to julian.zaidi@ubisoft.com.

© [2023] Ubisoft Entertainment. All Rights Reserved
