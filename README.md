#  MLPerf Benchmark Results in the MLCommons CM format

This repository contains compacted and aggregated results of the [MLPerf Inference benchmark]( https://github.com/mlcommons/inference ),
[MLPerf Training benchmark]() and [TinyMLPerf benchmark](https://github.com/mlcommons/tiny) 
in the compact [MLCommons Collective Mind format](https://github.com/mlcommons/ck)
for the [MLCommons CK Playground](https://x.cKnowledge.org)
being developed by the [MLCommons taskforce on automation and reproducibility](https://cKnowledge.org/mlcommons-taskforce).

The goal is to make it easier for the community to analyze MLPerf results, 
add derived metrics such as performance/Watt and constraints,
generate graphs, prepare reports and link reproducibility reports as shown in these examples:
* [Power efficiency to compare Qualcomm, Nvidia and Sima.ai devices](https://cKnowledge.org/mlcommons-mlperf-inference-gui-derived-metrics-and-conditions)
* [Reproducibility report for Nvidia Orin](https://access.cknowledge.org/playground/?action=experiments&name=mlperf-inference--v3.0--edge--closed--image-classification--offline&result_uid=3751b230c800434a)

## How to import raw MLPerf results to CK/CM format

Install [MLCommons CM framework](https://github.com/mlcommons/ck/blob/master/docs/installation.md).

### MLPerf inference benchmark results

Follow this [README](https://github.com/mlcommons/ck/blob/master/cm-mlops/script/import-mlperf-inference-to-experiment/README-extra.md) from the related CM automations script.

You can see aggregated results [here](https://access.cknowledge.org/playground/?action=experiments&tags=mlperf-inference,all).

### TinyMLPerf benchmark results

Follow this [README](https://github.com/mlcommons/ck/blob/master/cm-mlops/script/import-mlperf-tiny-to-experiment/README-extra.md) from the related CM automations script.

You can see aggregated results [here](https://access.cknowledge.org/playground/?action=experiments&tags=mlperf-tiny,all).

### MLPerf training benchmark results

Follow this [README](https://github.com/mlcommons/ck/blob/master/cm-mlops/script/import-mlperf-training-to-experiment/README-extra.md) from the related CM automations script.

You can see aggregated results [here](https://access.cknowledge.org/playground/?action=experiments&tags=mlperf-training,all).


## How to update this repository with new results

### Using your own Python script

You can use this repository to analyze, reuse, update and improve MLPerf results
compact
by calculating and adding derived metrics (performance/watt)
or links to reproducibility reports that will be visible at the [MLCommons CK playground](https://access.cknowledge.org/playground/?action=experiments).

Install [MLCommons CM framework](https://github.com/mlcommons/ck/blob/master/docs/installation.md).

Pull CM repository with automation recipes and with MLPerf results in the CM format:
```bash
cm pull repo mlcommons@ck
cm pull repo mlcommons@cm4mlperf-results
```

Find CM entries with MLPerf inference v3.1 experiments from CMD:
```bash
cm find experiment --tags=mlperf-inference,v3.1
```

Find CM entries with MLPerf inference v3.1 experiments from Python:
```python
import cmind

r = cmind.access({'action':'find',
                  'automation':'experiment,a0a2d123ef064bcb',
                  'tags':'mlperf-inference,v3.1'})

if r['return']>0: cmind.error(r)

lst = r['list']

for experiment in lst:
    print (experiment.path)
```

### Using CM script

We created a [sample CM script](script/process-mlperf-inference-results) in this repository 
that you can use and [extend](script/process-mlperf-inference-results/customize.py) to add derived metrics:

```bash
cm run script "process mlperf-inference results" --experiment_tags=mlperf-inference,v3.1
```




## Copyright

2021-2023 [MLCommons](https://mlcommons.org)

## License

[Apache 2.0](LICENSE.md)

## Project coordinators

[Grigori Fursin](https://cKnowledge.org/gfursin) and [Arjun Suresh](https://www.linkedin.com/in/arjunsuresh).

## Contact us

This project is maintained by the [MLCommons taskforce on automation and reproducibility](https://cKnowledge.org/mlcommons-taskforce),
[cTuning foundation](https://cTuning.org) and [cKnowledge.org](https://cKnowledge.org).

Join our [Discord server](https://discord.gg/JjWNWXKxwT) to ask questions, provide your feedback and participate in further developments.
