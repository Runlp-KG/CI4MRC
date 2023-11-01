## 2023 ACL(Finding) "Causal Intervention for Mitigating Name Bias in Machine Reading Comprehension"

## Reqirements:

* torch
* transformers


## Data process

The test data can be generated by the codes in the data_process directory.


## NEURON

we first construct a co-activation graph by `adj.py`.

Then, we use [METIS](http://glaros.dtc.umn.edu/gkhome/metis/metis/download) to split the graph into subgraphs.
```
gpmetis transformer.layer.{}.ff.layer_1.weight num_expert
```
where `num_expert` is the number of experts.

Finally, we balance the neurons in each expert by trans_gp.py.

We train a multi-layer perceptron. The details of the implementation can be found in `mlp_select_example.py`.

## TRAIN 

run_qa_beam_search_no_trainer.py for XLNet and run_qa_no_trainer.py for others.


## Cite
@inproceedings{DBLP:conf/acl/ZhuWZH023,
  
  author       = {Jiazheng Zhu, Shaojuan Wu, Xiaowang Zhang, Yuexian Hou and Zhiyong Feng},
  
  title        = {Causal Intervention for Mitigating Name Bias in Machine Reading Comprehension},
  
  booktitle    = {Findings of the Association for Computational Linguistics (ACL)},
  
  pages        = {12837--12852},
  
  publisher    = {Association for Computational Linguistics},
  
  year         = {2023},
  
  url          = {https://doi.org/10.18653/v1/2023.findings-acl.812},
  
  doi          = {10.18653/V1/2023.FINDINGS-ACL.812},
  
  biburl       = {https://dblp.org/rec/conf/acl/ZhuWZH023.bib},
  
  bibsource    = {dblp computer science bibliography, https://dblp.org}

}



