# IFBench

* NOTE: This IFBench implementation is based on PR [#3642](https://github.com/EleutherAI/lm-evaluation-harness/pull/3642) from the upstream `lm-evaluation-harness` repository.

### Paper

Generalizing Verifiable Instruction Following
[Abstract: https://arxiv.org/abs/2507.02833](https://arxiv.org/abs/2507.02833)

A crucial factor for successful human and AI interaction is the ability of language models or chatbots to follow human instructions precisely. A common feature of instructions are output constraints like ``only answer with yes or no" or ``mention the word `abrakadabra' at least 3 times" that the user adds to craft a more useful answer. Even today's strongest models struggle with fulfilling such constraints. We find that most models strongly overfit on a small set of verifiable constraints from the benchmarks that test these abilities, a skill called precise instruction following, and are not able to generalize well to unseen output constraints. We introduce a new benchmark, IFBench, to evaluate precise instruction following generalization on 58 new, diverse, and challenging verifiable out-of-domain constraints. In addition, we perform an extensive analysis of how and on what data models can be trained to improve precise instruction following generalization. Specifically, we carefully design constraint verification modules and show that reinforcement learning with verifiable rewards (RLVR) significantly improves instruction following. In addition to IFBench, we release 29 additional new hand-annotated training constraints and verification functions, RLVR training prompts, and code.

Homepage: https://github.com/allenai/IFBench/tree/main

### Implementation

`instructions.py` and `instructions_util.py` are vendored from
[`allenai/IFBench@db69a6f`](https://github.com/allenai/IFBench/tree/db69a6f05689830b0068b8f1529ebcfd2f3b164c).
The task YAML, result processing, and registry composition are lm-eval integrations.
Classic IFEval verifiers are reused from `lm_eval.tasks.ifeval`.


### Citation

```
@misc{pyatkin2025generalizing,
   title={Generalizing Verifiable Instruction Following},
   author={Valentina Pyatkin and Saumya Malik and Victoria Graf and Hamish Ivison and Shengyi Huang and Pradeep Dasigi and Nathan Lambert and Hannaneh Hajishirzi},
  journal={Advances in Neural Information Processing Systems},
  volume={38},
  year={2025}
}
```

### Groups and Tasks

#### Groups

* Not part of a group yet

#### Tasks

* `ifbench` : IFBench metrics from the [test dataset](https://huggingface.co/datasets/allenai/IFBench_test), this is the "base" metric.
* `ifbench_ifbench-constraints_single-turn` : Single-turn (`prompt` only) using partition `ifbench_constraints` from the [allenai/IFBench_multi-turn](https://huggingface.co/datasets/allenai/IFBench_multi-turn) dataset.
* `ifbench_ifeval-constraints_single-turn` : Single-turn (`prompt` only) using partition `ifeval_constraints` from the [allenai/IFBench_multi-turn](https://huggingface.co/datasets/allenai/IFBench_multi-turn) dataset.


### Checklist

For adding novel benchmarks/datasets to the library:
* [x] Is the task an existing benchmark in the literature?
  * [x] Have you referenced the original paper that introduced the task?
  * [x] If yes, does the original paper provide a reference implementation? If so, have you checked against the reference implementation and documented how to run such a test?


If other tasks on this dataset are already supported:
* [ ] Is the "Main" variant of this task clearly denoted?
* [ ] Have you provided a short sentence in a README on what each new variant adds / evaluates?
* [ ] Have you noted which, if any, published evaluation setups are matched by this variant?
