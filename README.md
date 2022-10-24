[English text below](#demutated-welsh-language-vector-model)

**Data: https://github.com/techiaith/word2vec-cy-demutated/tags**

# Model Iaith Fectorau Dad-dreigledig Cymraeg

Dyma fersiwn wedi'i ddad-dreiglo o'n model iaith word2vec Cymraeg. Hyfforddwyd y model ar gorpws ymchwil mewnol yr Uned Technolegau Iaith. Cyn hyfforddi'r model, rhagbroseswyd y corpws drwy geisio dad-dreiglo pob geirffurf treigladwy o'i ffurf dreigledig i'w ffurf gysefin.

Mae treiglo yn ffenomen seinegol sy'n effeithio ar lawer o eiriau Cymraeg ac sy'n golygu y gall eu llythrennau cyntaf newid (e.e. gyda 'caru' (=love) yn gallu bodoli fel 'garu', 'charu', a 'ngharu') heb fod newid i ystyr y gair.

Oherwydd hynny, mae'n ddymunol anwybyddu'r treigladau wrth hyfforddi fel na chaiff y geiriau sy'n treiglo eu trin yn wahanol i'r geiriau nad ydynt yn treiglo, a bod mwy o gysondeb rhwng mewnblaniadau Cymraeg a mewnblaniadau ieithoedd eraill lle nad yw'r geiriau'n treiglo.


I ddangos y gwahaniaeth yn y canlyniadau, dyma ganlyniadau chwilio am eiriau tebyg i 'caru' gan ddefnyddio ein model blaenorol:

```
model.wv.most_similar('caru') # geirffurfiau mwyaf tebyg i 'caru'

[('casáu', 0.7771924138069153), # hate
 ('garu', 0.7656854391098022), # mutated form of 'caru'
 ('edmygu', 0.7000856995582581), # admire
 ('hoffi', 0.6989531517028809), # like
 ('charu', 0.6611705422401428), # mutated form of 'caru'
 ('hedmygu', 0.5696538090705872), # mutated form of 'edmygu' (=admire)
 ('mwynhau', 0.5679166913032532), # enjoy
 ('casau', 0.5578843355178833), # hate
 ('gwerthfawrogi', 0.5516526103019714), # appreciate
 ('ddwli', 0.5482629537582397)] # mutated form of 'dwli' (=infatuate)
 ```

Sylwer bod 'garu' a 'charu', sy'n ffurfiau treigledig ar 'caru', yn cymryd 2 safle o fewn y 5 uchaf. 

Dyma enghraifft o'r model newydd a hyfforddwyd ar gorpws sydd wedi ei ddad-dreiglo.

```
model.wv.most_similar('caru') # geirffurfiau mwyaf tebyg i 'caru'

[('casáu', 0.6713356971740723), # to hate
 ('edmygu', 0.6115822196006775), # to admire
 ('cariad', 0.5292474031448364), # love
 ('cenfigennus', 0.4978679120540619), # jealous
 ('trystio', 0.4932989478111267), # to trust
 ('melltithio', 0.47602102160453796), # to curse
 ('ddwli', 0.4717932343482971), # to dote
 ('cysuro', 0.46681320667266846), # to comfort
 ('ymserchu', 0.46169954538345337), # to infatuate
 ('swyno', 0.45901909470558167)] # to charm
```

Sylwer bod y ffurfiau treigledig ar 'caru', sef 'garu' a 'charu', bellach wedi diflannu o'r rhestr, gan roi mwy o le yn y rhestr i eiriau gyda gwahanol ystyron.

Mae'n werth nodi hefyd bod y canlyniadau wedi newid yn fwy eang na hynny, gyda ffurfiau mwy cyffredinol fel 'hoffi' a 'gwerthfawrogi' yn llithro allan o'r canlyniadau. Mae ffurfiau fel 'casáu' a 'melltithio' yn dangos y gall gwrthystyron feddu ar fewnblaniadau tebyg iawn i fewnblaniad y gair sydd dan sylw. Mae hyn oherwydd bod gwrthystyron fel 'caru' a 'casáu' yn digwydd o fewn brawddegau gyda strwythuron tebyg. Er cymhariaeth, mae 'hate' a despise' yn codi'n uchel yng nghanlyniadau fectorau Saesneg Google News wrth chwilio am eiriau tebyg i 'love'.

O ganlyniad, credwn fod y canlyniadau hyn yn fwy tebyg i allbwn iaith fel y Saesneg lle nad yw geiriau'n treiglo. Credwn hefyd fod y canlyniadau yn fwy cyson gan fod mewnblaniadau geiriau treigladwy a geiriau annhreigladwy yn fwy cael eu cynhyrchu mewn modd mwy rheolaidd, er bod lle i wella er mwyn sicrhau bod y dad-dreiglo yn digwydd yn fwy trylwyr.

Nid yw'r model hwn o reidrwydd yn 'well' na'r un sydd heb ddad-dreiglo; bydd yr un sydd fwyaf priodol yn dibynnu ar y defnydd a fwriedir ei wneud o'r model.

## Nodiadau

### Ffurfiau lluosog a ffurfiau berfol
Penderfynwyd peidio ¾a dad-luosogi enwau gan fod ystyr enw unigol fel _cath_ (=cat) yn gysyniadol wahanol ei ystyr i'w ffurf luosog _cathod_ (=cats). Yn yr un modd, ni chafodd ffurfiau berfol eu dad-redeg - dim ond eu dad-dreiglo, gan y teimlwn fod gwahniaethau o ran yn amser a pheson y ffurfiau hyn yn newid eu hystyr. O ganlyniad, newidiwyd pob _redais_ (=I ran) i _rhedais_ yn hytrach na _rhedeg_.

### Llythrennau bach
Troswyd y ffurfiau oll i lythrennau bach yn y fersiwn hwn o'r model.  

### Geirffurfiau amwys eu dad-dreiglad
Gall fod yn anodd dad-dreiglo rhai geirffurfiau yn briodol gan fod eu ffurfiau yn amwys. Er enghraifft, gall _law_ gynrychioli ffurf dreigledig ar _glaw_ (=rain) neu _llaw_ (=hand), ac nid yw'n fater mor syml i'w dad-dreiglo yn briodol. Yn ogystal, gall geirffurfiau treigledig wrthdaro gyda geirffurfiau di-dreiglad, er enghraifft 'chi' (ffurf dreigledig ar 'ci' (=dog)), a'r rhagenw 'chi' (=you, plural/formal). 

Am y tro, penderfynwyd cadw rhain heb eu treiglo, gan ystyried ei bod yn well eu cadw fel yr oeddynt na cheisio eu dad-dreiglo, ond gyda pherygl o wneud hynny'n anghywir. Byddwn yn ymchwilio i wahanol ddulliau o ddad-dreiglo yn gywir yn ¾ol y cyd-destun.

## Defnyddio

I ddefnyddio'r model hwn:

```
import gensim
from gensim.models import Word2Vec

model = Word2Vec.load("model_221021_demutate")

caru_count = model.wv.get_vecattr("caru", "count")
print (caru_count) #70926

caru_most_similar = model.wv.most_similar('caru')
print (caru_most_similar)

# [('casáu', 0.6713356971740723),
#  ('edmygu', 0.6115822196006775),
#  ('cariad', 0.5292474031448364),
#  ('cenfigennus', 0.4978679120540619),
#  ('trystio', 0.4932989478111267),
#  ('melltithio', 0.47602102160453796),
#  ('ddwli', 0.4717932343482971),
#  ('cysuro', 0.46681320667266846),
#  ('ymserchu', 0.46169954538345337),
#  ('swyno', 0.45901909470558167)]
```

*Gweler https://github.com/techiaith/word2vec-cy-demutated/tags ac yna clicio ar 'Latest' i gael mynediad at y data.*

*Ariannwyd creu'r model hwn gan Lywodraeth Cymru.*

# Demutated Welsh-language Vector Model

This is a de-mutated version of our word2vec Welsh-language model. The model was trained on the Language Technologies Unit's large internal research corpus. Before training the model, the corpus was pre-processed by attempting to de-mutate each mutable word form found in the corpus from its mutated form to its radical form.

Mutation is a phonetic phenomenon that affects many Welsh words and means that their first letters can change (so that 'caru' (=love) can exist as 'garu', 'caru', and 'caru' ') without any change in the word's meaning.

As a result, it is desirable to ignore these mutations when training so that the words that can undergo mutattion are not treated differently to the words that cannot mutate. This also ensures that there is more consistency between Welsh-language embeddings and the embeddings of other languages ​​which do not feature such mutations.

Here are the results of our previous model.


```
model.wv.most_similar('caru') # geirffurfiau mwyaf tebyg i 'caru'

[('casáu', 0.7771924138069153), # hate
 ('garu', 0.7656854391098022), # mutated form of 'caru'
 ('edmygu', 0.7000856995582581), # admire
 ('hoffi', 0.6989531517028809), # like
 ('charu', 0.6611705422401428), # mutated form of 'caru'
 ('hedmygu', 0.5696538090705872), # mutated form of 'edmygu' (=admire)
 ('mwynhau', 0.5679166913032532), # enjoy
 ('casau', 0.5578843355178833), # hate
 ('gwerthfawrogi', 0.5516526103019714), # appreciate
 ('ddwli', 0.5482629537582397)] # mutated form of 'dwli' (=infatuate)
 ```

Note that 'garu' and 'caru', which are mutated forms of 'caru', take 2 positions within the top 5.

Here is an example of the new model trained on the de-mutated corpus.

```
model.wv.most_similar('caru') # geirffurfiau mwyaf tebyg i 'caru'

[('casáu', 0.6713356971740723), # to hate
 ('edmygu', 0.6115822196006775), # to admire
 ('cariad', 0.5292474031448364), # love
 ('cenfigennus', 0.4978679120540619), # jealous
 ('trystio', 0.4932989478111267), # to trust
 ('melltithio', 0.47602102160453796), # to curse
 ('ddwli', 0.4717932343482971), # to dote
 ('cysuro', 0.46681320667266846), # to comfort
 ('ymserchu', 0.46169954538345337), # to infatuate
 ('swyno', 0.45901909470558167)] # to charm
```

Note that the mutated forms of 'caru', namely 'garu' and 'caru', have now disappeared from the list, providing more space for words with different meanings.

It is also worth noting that the results have also changed more widely, with more general forms such as 'hoffi' ('like') and 'gwerthfawrogi' ('appreciate') slipping out of the results to be replaced by more specific forms such as 'cysuro' ('to comfort'). The inclusion of forms such as 'melltithio' ('to curse') and 'casáu' ('to hate') show that similar embeddings exist for antonyms, even though they mean the opposite. This is primarily due to antonyms such as 'love' and 'hate' occuring within sentences which have very similar structures. It should be noted that 'hate' and 'despise' feature high in the results of Google News English vectors for words similar to 'love'.

We therefore believe that these results are more similar to the output of a language such as English where words do not mutate. We also believe that the results are more internally consistent as the implants of mutable words and non-mutable words are now produced in a more regular manner (although there is room for improvement to ensure that the de-mutation takes place more thoroughly).

Note that this model is not necessarily 'better' than the one without demutation; the most appropriate model for your task will depend on the intended use of the model.

## Notes

### Plural forms and verbal forms
It was decided not to de-pluralize nouns as the meaning of a singular noun like _cath_ (=cat) is conceptually different in meaning from its plural form _cathod_ (=cats). Similarly, verbal forms were not de-conjugated, but rather only de-mutated, as we feel that the differences in the tense and person of these forms change their meaning. As a result, all examples of _redais_ (=I ran) were changed to the verbal _rhedais_ instead of the verbnoun and lemma _rhedeg_.

### Lower case
All forms were lowercased for this model.  

### Wordforms with ambiguous demutations
Some word forms can be difficult to de-mute appropriately in isolation as their appropriate demutated forms can be ambiguous. For example, _law_ can represent a mutated form of _glaw_ (=rain) or of _llaw_ (=hand), and it is not a simple matter to identify the appropriate demutation. In addition, mutated wordforms may also conflict with unmutated wordforms, as is the case with 'chi' (a mutated form of 'ci' (=dog)), and the pronoun 'chi' (=you, plural/formal). 

For the time being we have to decided not to attempt to demutate ambiguous forms, judging it better to not demutate thatn to demutate incorrectly. In the future, we will investigate different methods of de-mutating appropriately according to context.

## Usage

```
import gensim
from gensim.models import Word2Vec

model = Word2Vec.load("model_221021_demutate")

caru_count = model.wv.get_vecattr("caru", "count")
print (caru_count) #70926

caru_most_similar = model.wv.most_similar('caru')
print (caru_most_similar)

# [('casáu', 0.6713356971740723),
#  ('edmygu', 0.6115822196006775),
#  ('cariad', 0.5292474031448364),
#  ('cenfigennus', 0.4978679120540619),
#  ('trystio', 0.4932989478111267),
#  ('melltithio', 0.47602102160453796),
#  ('ddwli', 0.4717932343482971),
#  ('cysuro', 0.46681320667266846),
#  ('ymserchu', 0.46169954538345337),
#  ('swyno', 0.45901909470558167)]
```

*See https://github.com/techiaith/word2vec-cy-demutated/tags and click on 'Latest' to access the data.*

*The creation of this model was financed by the Welsh Government.*

