# foldit_tree_visualization
Requirements:
* Python3 and the following packages
* graphviz
* matplotlib (only for getting the Tableau color palette in the `output_tree` function in [`make_tree_viz.py`](make_tree_viz.py))
* editdistance (only for scaling edge width by sequence difference in the `output_tree_helper` function in [`make_tree_viz.py`](make_tree_viz.py))
* numpy
* scipy

Usage:
`python3 make_tree_viz.py [--viz] [--evolver] [--uid UID] RANKS_FILE PIDS`

`--viz` the script will generate tree visualizations. Output directory specified in the `dot.render` call in the `output_tree` function in [`make_tree_viz.py`](make_tree_viz.py)</br>
`--evolver` if `--uid` is given, the trees will include nodes from evolvers</br>
`--uid UID` generate trees for user with uid of `UID`, otherwise trees will be generated for the top 15 soloists, and soloists ranked 36 through 50</br>
`RANKS_FILE` the path to a csv dump of the `rprp_puzzle_ranks` table in the Foldit database
`PIDS` one or more puzzle ids to generate trees for

In addition to the ranks file, you will need csv files for the solution data and the history data for each puzzle in whatever subdirectory the `datapath` function in [`make_tree_viz.py`](make_tree_viz.py) specifies.
Running the script will generate pickled versions of these files in order to save time on future runs.

File | Description 
--- | ---
[`RawNode.py`](RawNode.py) | Code for generating the raw solution trees as well as a number of useful operations related to that
[`Node.py`](Node.py) | Class representing a solution tree, takes a `RawNode` as input. This class includes the tree summarization functions.
[`tree_analysis.py`](tree_analysis.py) | Collection of functions for detecting and quantifiying various solver behaviors
[`make_tree_viz.py`](make_tree_viz.py) | Main script, loads the csv data and genereates visualizations. Code for labeling nodes with macro ids or as containing a manual-only action has been commented out.
