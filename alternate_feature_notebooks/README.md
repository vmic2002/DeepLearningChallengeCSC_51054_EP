## Notes for running alternate feature notebooks
The notebooks used for alternate feature representations use an additional library not required for the main notebook, `swifter`, which is just used to speed up some processing of dataframes through parallelization. It can be installed using
```pip install swifter```

These notebooks also assume a gpu present on the system, which is accessed using `cuda:1` (i.e., the code will work without modification only if there is more than one CUDA device present). To change this, change the line in each that says:
`gpu = torch.device('cuda:1')`
to whichever device you would like to run on.

In addition, these notebooks assume the presence of a folder named `submissions` in this folder.

The notebooks for which these notes apply are:
 * `mean_stdev_agg.ipynb`
 * `n_gram_vectors.ipynb`
 * `long_match_sequence.ipynb`
 * `period_sequence.ipynb`

Note that these notebooks were created primarily to run experiments, and thus are not thoroughly edited for readability.