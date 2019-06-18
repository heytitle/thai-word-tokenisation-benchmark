# Word Tokenisation Benchmark for Thai

## Objective
This repository is a framework for benchmarking tokenisation algorithms for Thai. It has a command-line interface that allows users to conviniently execute the benchmarks as well as a module interface for later use in their development pipelines.

<div align="center">
    <img src="https://i.imgur.com/jVBOLa2.png"/>
</div>

## Metrics
### Character-Level
- True Positive (TP): no. of starting characters that are correctly predicted.
- True Negative (TN): no. of non-starting characters that are correctly predicted.
- False Positive (FP): no. of non-starting characters that are wrongly predicted as starting characters.
- False Negative (FN): no. of starting characters that are wrongly predicted as non-starting characters.
- Precision: TP / (TP + FP)
- Recall: TP / (TP+FN)
- f1: ...
### Word-Level
- Correctly Tokenised Words (CTW): no. of words in reference that are correctly tokenised.
- Precision: CTW / no. words in reference solution
- Recall: CTW / no. words in sample
-**** f1: ...

## Installation (TBD)
```
pip ...
```

## Usages (to be updated)
1. Command-line Interface 
    ```
    PYTHONPATH=`pwd` python scripts/thai-tokenisation-benchmark.py \
    --test-file ./data/best-2010/TEST_100K_ANS.txt \
    --input ./data/best-2010-syllable.txt

    # Sample output
    Benchmarking ./data/best-2010-deepcut.txt against ./data/best-2010/TEST_100K_ANS.txt with 2252 samples in total
    ============== Benchmark Result ==============
                    metric       mean±std       min    max
             char_level:tp    47.82±47.22  1.000000  354.0
             char_level:tn  144.19±145.97  1.000000  887.0
             char_level:fp      1.34±2.02  0.000000   23.0
             char_level:fn      0.70±1.19  0.000000   14.0
      char_level:precision      0.96±0.08  0.250000    1.0
         char_level:recall      0.98±0.04  0.500000    1.0
             char_level:f1      0.97±0.06  0.333333    1.0
      word_level:precision      0.92±0.14  0.000000    1.0
         word_level:recall      0.93±0.12  0.000000    1.0
             word_level:f1      0.93±0.13  0.000000    1.0
    ```

2. Module Interface
    ```
    from pythainlp.benchmarks import word_tokenisation as bwt

    ref_samples = array of reference tokenised samples
    tokenised_samples = array of tokenised samples, aka. from your algorithm

    # dataframe contains metrics for each sample
    df = bwt.benchmark(ref_samples, tokenised_samples)
    ```

## Developments
```
# unitests
$ TEST_VERBOSE=1 PYTHONPATH=. python tests/__init__.py
```

## Acknowledgements
TBD.