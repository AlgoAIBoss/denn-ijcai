# DENN
Experiments for the paper _DENN_, _Handling Black Swan Events in Deep Learning with Diversely Extrapolated Neural Networks_, published at IJCAI 2020.

# Datasets

Feel free to contact me if you want me to send the .h5 versions of the imitation datasets.

# Regression
- The ``.sh`` files to train the different models are available in ``exec/`` for each experiment.
- The figures can be generated using the Jupyter notebooks.

# Classification
- The datasets need to be downloaded first.
- The figures can be generated using the Jupyter notebook.
- To train the models, use the files in this order for each model:

## DENN
1. train_reference.sh
2. train_denn.sh
3. compute_stats_denn.sh 

## Deep ensemble
1. train_ensemble.sh
2. compute_stats_ensemble.sh

## Prior
1. train_prior.sh
2. compute_stats_prior.sh

## Anchoring
1. train_anchoring.sh
2. compute_stats_anchoring.sh

## OE
1. train_oe.sh
2. compute_stats_oe.sh

Note: the different methods were adapted to fit the same common framework (same optimizer, same repulsive frames) and compare the additional term in the loss that they provide.

# Imitation learning
Repository #1: https://github.com/sanjaythakur/trpo
Repository #2: https://github.com/sanjaythakur/Multiple_Task_MuJoCo_Domains

- Train a PPO agent on Reacher-v1 using the code and default parameters available at Repository #1
  The trained agent is saved in folder `saved_models/`
  ``./train.py Reacher-v1 -n 60000 -b 50``
- To create the datasets, you first need to modify the xml files in MuJoCo defining modifying the Reacher environment.
Follow the instructions given in the Repository #2 above and the prepared xml files in `src/`. You should find the xml files in:
``envs/YOUR_ENV_NAME/lib/python3.7/site-packages/gym/envs/mujoco/assets/ ``
Then, create trajectories datasets (a graphic interface is required, ssh is NOT enough), launch: 
  ``python px_color_create_trajs.py —color red —shape sphere``
- To train a reference function on the chosen dataset, launch:
  ``bash exec/train_reference.sh``
  . Note: modify the dataset to use in the ``.sh`` file.
- To train the ensemble, launch: 
  ``bash exec/train_ensemble.sh``
  . Note: modify the dataset to use in the ``.sh`` file.
- To train DENN, launch: 
  ``bash exec/train_denn.sh``
  . Note: modify the datasets to use in the ``.sh`` file.
- To compute statistics and generate the figures, use the ``.sh`` files in ``exec/``. Use the ``--final`` flag to compute stats on the test set rather than the validation set. 
- To generate the figures, use the Jupyter notebook
