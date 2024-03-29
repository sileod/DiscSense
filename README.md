# DiscSense: Automated Semantic Analysis of Discourse Markers

This is a data/code release accompanying this paper:

- Title: "DiscSense: Automated Semantic Analysis of Discourse Markers"
- Authors: Damien Sileo, Tim Van de Cruys, Camille Pradel and Philippe Muller

# Contents

Discourse markers can be considered as noisy labels for various semantic tasks, such as entailment (y=*therefore*), subjectivity analysis (y=*personally*) or sentiment analysis (y=*sadly*), similarity (y=*similarly*), typicality, (y=*curiously*) ...

DiscSense provides a set of associations between discourse markers and the classes of various tasks.

Unlike previous work on discourse marker semantics, DiscSense was built automatically: we finetuned a BERT model for discourse marker prediction between sentences (using the [Discovery](https://github.com/synapse-developpement/Discovery) dataset) and used the marker prediction between sentences of existing datasets. This allows us to measure associations between the classes of existing datasets and predicted markers. 
Previous work mainly use PDTB discourse relations to characterize discourse markere; here, we use a much broader range of linguistic phenomena, by leveraging the datasets of [DiscEval](<https://github.com/synapse-developpement/DiscEval>), [SentEval](https://github.com/facebookresearch/SentEval) and [GLUE](http://gluebenchmark.com/) evaluation benchmarks.



This repository contains an association table with 2.9k associations.
The following table is a small sample showing the dataset classes available in DiscSense alongside the 2 most associated markers. 
For instance, in the CR dataset, when "sadly" is the most plausible marker beginning a sentence, it has 95.2% chance of being annotated with negative sentiment.

```
marker            class                                         support  confidence (prior)
----------------  ------------------------------------------  ---------  --------------------
unfortunately,    CR.negative                                        66  100.0 (36.6)
sadly,            CR.negative                                        20  95.2 (36.6)
regardless,       CR.positive                                        31  96.9 (63.4)
fortunately,      CR.positive                                        27  96.4 (63.4)
meaning,          Cola.not-well-formed                               21  48.8 (29.7)
on_the_contrary,  Cola.not-well-formed                               50  45.9 (29.7)
regardless,       Cola.well-formed                                   23  95.8 (70.3)
undoubtedly,      Cola.well-formed                                   25  92.6 (70.3)
only,             Emergent.against                                   24  88.9 (15.5)
meantime,         Emergent.against                                   21  24.1 (15.5)
normally,         Emergent.for                                       22  78.6 (47.5)
later,            Emergent.for                                       89  78.1 (47.5)
separately,       Emergent.observing                                148  59.2 (37.0)
now,              Emergent.observing                                 35  50.0 (37.0)
anyway,           EmoBankArousal.high                                24  85.7 (48.5)
suddenly,         EmoBankArousal.high                               103  73.6 (48.5)
originally,       EmoBankArousal.low                                 27  90.0 (51.5)
presently,        EmoBankArousal.low                                 24  80.0 (51.5)
together,         EmoBankDominance.high                              20  62.5 (38.7)
absolutely,       EmoBankDominance.high                              68  62.4 (38.7)
inevitably,       EmoBankDominance.low                               21  91.3 (61.3)
only,             EmoBankDominance.low                               31  81.6 (61.3)
plus,             EmoBankValence.high                                45  90.0 (43.2)
hopefully,        EmoBankValence.high                                26  86.7 (43.2)
sadly,            EmoBankValence.low                                 36  92.3 (56.8)
frankly,          EmoBankValence.low                                 33  89.2 (56.8)
separately,       Formality.high                                    295  100.0 (48.2)
significantly,    Formality.high                                     73  100.0 (48.2)
well,             Formality.low                                      49  100.0 (51.8)
seriously,        Formality.low                                      35  100.0 (51.8)
this,             GUM.circumstance                                   24  35.3 (57.8)
especially,       GUM.circumstance                                   40  30.5 (57.8)
or,               GUM.condition                                      31  50.0 (42.2)
especially,       GUM.condition                                      41  31.3 (42.2)
instead,          Implicature.high                                   28  77.8 (46.7)
absolutely,       Implicature.high                                   36  70.6 (46.7)
by_comparison,    Implicature.low                                    24  88.9 (53.3)
strangely,        Implicature.low                                    22  81.5 (53.3)
significantly,    Informativeness.high                               57  100.0 (46.3)
altogether,       Informativeness.high                               31  100.0 (46.3)
seriously,        Informativeness.low                                37  100.0 (53.7)
really,           Informativeness.low                                25  100.0 (53.7)
in_contrast,      MNLI.contradiction                               1182  74.1 (33.3)
curiously,        MNLI.contradiction                               2912  70.8 (33.3)
in_turn,          MNLI.entailment                                  7475  65.4 (33.4)
likewise,         MNLI.entailment                                  2430  63.0 (33.4)
for_instance      MNLI.neutral                                      177  70.8 (33.3)
for_example       MNLI.neutral                                      170  70.0 (33.3)
so,               MRDA.Accept                                        57  12.9 (3.1)
well,             MRDA.Acknowledge-answer                            85  10.3 (3.6)
well,             MRDA.Action-directive                              20  2.4 (1.5)
actually,         MRDA.Affirmative Non-yes Answers                   37  12.2 (3.0)
personally,       MRDA.Assessment/Appreciation                       25  15.9 (4.0)
especially,       MRDA.Collaborative Completion                      25  7.4 (2.2)
really,           MRDA.Declarative-Question                          48  11.9 (1.4)
mostly,           MRDA.Defending/Explanation                        114  62.3 (10.9)
probably,         MRDA.Dispreferred Answers                          25  1.5 (1.3)
namely,           MRDA.Expansions of y/n Answers                     37  33.6 (8.5)
so,               MRDA.Floor Grabber                                 56  12.7 (4.4)
and               MRDA.Floor Holder                                  53  8.2 (4.9)
and               MRDA.Hold Before Answer/Agreement                  26  4.0 (1.1)
absolutely,       MRDA.Interrupted/Abandoned/Uninterpretable         24  1.2 (1.2)
probably,         MRDA.Negative Non-no Answers                       28  1.7 (0.9)
though,           MRDA.Offer                                         27  18.9 (7.1)
honestly,         MRDA.Other Answers                                 31  36.0 (1.2)
actually,         MRDA.Reject                                        34  11.2 (0.9)
probably,         MRDA.Reject-part                                   20  1.2 (0.3)
also,             MRDA.Rising Tone                                   66  36.7 (7.0)
originally,       MRDA.Statement                                     20  37.0 (22.1)
surely,           MRDA.Understanding Check                           26  40.6 (5.2)
realistically,    MRDA.Wh-Question                                   24  27.6 (2.3)
or,               MRDA.Yes-No-question                               61  16.1 (1.7)
elsewhere,        MRPC.not-paraphrase                                30  81.1 (32.5)
meanwhile,        MRPC.not-paraphrase                                21  61.8 (32.5)
similarly,        MRPC.paraphrase                                    85  87.6 (67.5)
likewise,         MRPC.paraphrase                                   103  84.4 (67.5)
rather,           PDTB.Alternative                                   36  25.4 (0.5)
instead,          PDTB.Alternative                                   27  22.5 (0.5)
then,             PDTB.Asynchronous                                  60  38.7 (1.9)
previously,       PDTB.Asynchronous                                  36  36.4 (1.9)
by_doing_this,    PDTB.Cause                                         22  61.1 (11.5)
so,               PDTB.Cause                                         38  55.9 (11.5)
but               PDTB.Comparison                                    97  52.4 (6.5)
however           PDTB.Comparison                                    27  38.6 (6.5)
additionally      PDTB.Conjunction                                   47  63.5 (9.7)
meanwhile,        PDTB.Conjunction                                  167  55.5 (9.7)
by_doing_this,    PDTB.Contingency                                   22  57.9 (11.7)
theoretically,    PDTB.Contingency                                   70  50.4 (11.7)
but               PDTB.Contrast                                      89  61.4 (5.4)
by_comparison,    PDTB.Contrast                                     214  45.4 (5.4)
currently,        PDTB.Entrel                                       212  63.5 (13.5)
generally,        PDTB.Entrel                                        31  53.4 (13.5)
for_instance      PDTB.Expansion                                    179  77.5 (23.4)
similarly,        PDTB.Expansion                                     47  74.6 (23.4)
for_instance      PDTB.Instantiation                                138  65.1 (3.7)
for_example       PDTB.Instantiation                                 32  51.6 (3.7)
elsewhere,        PDTB.List                                          41  16.2 (1.0)
meanwhile,        PDTB.List                                          25  8.3 (1.0)
specifically,     PDTB.Restatement                                  100  67.6 (8.3)
essentially,      PDTB.Restatement                                   61  54.5 (8.3)
separately,       PDTB.Synchrony                                     21  2.8 (0.5)
then,             PDTB.Temporal                                      62  36.7 (2.4)
later,            PDTB.Temporal                                      44  31.2 (2.4)
moreover          PersuasivenessEloquence.high                       21  46.7 (26.5)
hence,            PersuasivenessEloquence.low                        21  84.0 (73.5)
by_doing_this,    PersuasivenessEloquence.low                        21  80.8 (73.5)
undoubtedly,      PersuasivenessPremiseType.common_knowledge         24  85.7 (100.0)
moreover          PersuasivenessPremiseType.common_knowledge         35  83.3 (100.0)
for_instance      PersuasivenessRelevance.high                       25  67.6 (59.9)
moreover          PersuasivenessRelevance.high                       29  64.4 (59.9)
undoubtedly,      PersuasivenessRelevance.low                        21  56.8 (40.1)
especially,       PersuasivenessRelevance.low                        20  37.0 (40.1)
for_instance      PersuasivenessSpecificity.high                     24  82.8 (45.9)
moreover          PersuasivenessSpecificity.high                     21  72.4 (45.9)
undoubtedly,      PersuasivenessSpecificity.low                      20  87.0 (54.1)
undoubtedly,      PersuasivenessStrength.low                         20  87.0 (100.0)
especially,       PersuasivenessStrength.low                         23  59.0 (100.0)
likewise,         QNLI.entailment                                    38  74.5 (50.0)
actually,         QNLI.entailment                                    48  68.6 (50.0)
regardless,       QNLI.not_entailment                                29  87.9 (50.0)
thirdly,          QNLI.not_entailment                                23  85.2 (50.0)
collectively,     QQP.duplicate                                      45  68.2 (36.9)
indeed,           QQP.duplicate                                     113  67.3 (36.9)
anyway,           QQP.not-duplicate                                  87  100.0 (63.1)
namely,           QQP.not-duplicate                                  50  100.0 (63.1)
technically,      RTE.entailment                                     56  72.7 (50.4)
in_turn,          RTE.entailment                                     83  66.9 (50.4)
by_comparison,    RTE.not_entailment                                 29  67.4 (49.6)
incidentally,     RTE.not_entailment                                 38  58.5 (49.6)
technically,      SICKE.contradiction                                29  87.9 (14.8)
rather,           SICKE.contradiction                               147  69.7 (14.8)
in_turn,          SICKE.entailment                                   32  64.0 (28.9)
alternately,      SICKE.entailment                                   93  59.6 (28.9)
meanwhile,        SICKE.neutral                                     155  92.8 (56.4)
elsewhere,        SICKE.neutral                                     765  89.8 (56.4)
unfortunately,    SST-2.negative                                    240  96.0 (44.3)
as_a_result,      SST-2.negative                                     65  94.2 (44.3)
nonetheless       SST-2.positive                                    383  93.4 (55.7)
nevertheless      SST-2.positive                                     56  90.3 (55.7)
so,               STAC.Acknowledgement                               40  21.3 (10.6)
absolutely,       STAC.Acknowledgement                              162  20.3 (10.6)
so,               STAC.Clarification_question                        23  12.2 (2.9)
really,           STAC.Clarification_question                        54  11.9 (2.9)
however           STAC.Comment                                       91  48.7 (10.9)
overall,          STAC.Comment                                       25  32.5 (10.9)
otherwise,        STAC.Conditional                                   21  25.0 (1.1)
anyway,           STAC.Continuation                                  52  10.4 (6.2)
and               STAC.Continuation                                  21  8.2 (6.2)
probably,         STAC.Contrast                                      76  18.9 (3.9)
maybe,            STAC.Contrast                                      35  18.3 (3.9)
alternately,      STAC.Elaboration                                   22  59.5 (7.7)
personally,       STAC.Elaboration                                   23  17.2 (7.7)
especially,       STAC.Explanation                                   21  12.4 (4.0)
anyway,           STAC.Explanation                                   36  7.2 (4.0)
really,           STAC.Q_Elab                                       147  32.5 (4.6)
or,               STAC.Q_Elab                                        41  19.3 (4.6)
surprisingly,     STAC.Question_answer_pair                          71  89.9 (19.7)
sadly,            STAC.Question_answer_pair                         249  77.3 (19.7)
finally,          STAC.Result                                       130  46.9 (6.3)
once,             STAC.Result                                        70  44.6 (6.3)
finally,          STAC.Sequence                                      29  10.5 (0.9)
currently,        STAC.no_relation                                   50  65.8 (21.3)
eventually,       STAC.no_relation                                   74  59.7 (21.3)
elsewhere,        STS.dissimilar                                    516  70.0 (43.5)
meantime,         STS.dissimilar                                    124  65.3 (43.5)
in_turn,          STS.similar                                       142  60.2 (56.5)
specifically,     STS.similar                                        25  51.0 (56.5)
presently,        SUBJ.objective                                     24  100.0 (49.8)
soon,             SUBJ.objective                                    159  99.4 (49.8)
frankly,          SUBJ.subjective                                   127  100.0 (50.2)
again,            SUBJ.subjective                                    65  100.0 (50.2)
technically,      Sarcasm.notsarcasm                                 34  72.3 (50.1)
secondly,         Sarcasm.notsarcasm                                 27  69.2 (50.1)
seriously,        Sarcasm.sarcasm                                   225  71.2 (49.9)
so,               Sarcasm.sarcasm                                    82  65.6 (49.9)
well,             SwitchBoard.Acknowledge (Backchannel)              30  2.8 (1.2)
seriously,        SwitchBoard.Action-directive                       25  4.6 (2.1)
only,             SwitchBoard.Affirmative Non-yes Answers            20  3.0 (1.7)
actually,         SwitchBoard.Agree/Accept                           64  17.3 (3.7)
actually,         SwitchBoard.Appreciation                           58  15.7 (4.7)
especially,       SwitchBoard.Collaborative Completion               38  10.1 (2.5)
anyway,           SwitchBoard.Conventional-closing                   82  39.4 (2.9)
surely,           SwitchBoard.Declarative Yes-No-Question            22  20.2 (4.0)
or,               SwitchBoard.Dispreferred Answers                   24  1.7 (0.6)
honestly,         SwitchBoard.Hedge                                  24  19.7 (1.6)
so,               SwitchBoard.Hold Before Answer/Agreement           24  2.5 (1.1)
only,             SwitchBoard.Negative Non-no Answers                43  6.4 (0.8)
so,               SwitchBoard.Open-Question                          85  8.8 (1.6)
well,             SwitchBoard.Other                                  36  3.4 (0.8)
or,               SwitchBoard.Other Answers                          25  1.8 (0.5)
absolutely,       SwitchBoard.Quotation                              89  6.2 (3.1)
especially,       SwitchBoard.Repeat-phrase                          24  6.4 (1.3)
or,               SwitchBoard.Rhetorical-Question                    48  3.4 (1.9)
so,               SwitchBoard.Self-talk                              22  2.3 (0.4)
really,           SwitchBoard.Signal-non-understanding               37  5.6 (0.5)
luckily,          SwitchBoard.Statement-non-opinion                  20  71.4 (15.6)
personally,       SwitchBoard.Statement-opinion                      43  20.4 (5.2)
meaning,          SwitchBoard.Summarize/Reformulate                  26  6.9 (3.0)
this,             SwitchBoard.Uninterpretable                       158  56.0 (19.2)
realistically,    SwitchBoard.Wh-Question                            48  33.8 (5.7)
incidentally,     SwitchBoard.Yes-No-Question                        32  78.0 (14.5)
coincidentally,   Verifiability.experiential                         20  80.0 (14.2)
recently,         Verifiability.experiential                         23  76.7 (14.2)
especially,       Verifiability.non-experiential                     36  39.1 (15.6)
unfortunately,    Verifiability.non-experiential                     28  22.8 (15.6)
third,            Verifiability.unverifiable                         23  100.0 (70.3)
ideally,          Verifiability.unverifiable                        227  99.6 (70.3)
```

# Instructions

The association table are available in the discsense folder in tsv format.

We used [mlxtend association rules module]( http://rasbt.github.io/mlxtend/user_guide/frequent_patterns/association_rules/>) to find associations.

# Citation

```
@inproceedings{sileo-etal-2020-discsense,
    title = "{D}isc{S}ense: Automated Semantic Analysis of Discourse Markers",
    author = "Sileo, Damien  and
      Van de Cruys, Tim  and
      Pradel, Camille  and
      Muller, Philippe",
    booktitle = "Proceedings of the 12th Language Resources and Evaluation Conference",
    month = may,
    year = "2020",
    address = "Marseille, France",
    publisher = "European Language Resources Association",
    url = "https://aclanthology.org/2020.lrec-1.125",
    pages = "991--999",
    language = "English",
    ISBN = "979-10-95546-34-4",
}
```


# Contact

For further information, you can contact:

damien dot sileo at gmail dot com
