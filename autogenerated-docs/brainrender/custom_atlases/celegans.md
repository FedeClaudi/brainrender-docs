



Contents
========

* [**Celegans**](#celegans)
	* [**`__init__`** [#62]](#__init__-62)
	* [**`_make_root`** [#84]](#_make_root-84)
	* [**`get_neurons_by`** [#119]](#get_neurons_by-119)
	* [**`get_neuron_color`** [#151]](#get_neuron_color-151)
	* [**`_get_data`** [#186]](#_get_data-186)
	* [**`_check_neuron_argument`** [#249]](#_check_neuron_argument-249)
	* [**`_parse_neuron_skeleton`** [#272]](#_parse_neuron_skeleton-272)
	* [**`_get_structure_mesh`** [#308]](#_get_structure_mesh-308)
	* [**`get_neurons`** [#329]](#get_neurons-329)
	* [**`get_neurons_synapses`** [#371]](#get_neurons_synapses-371)
	* [**`dist`** [#518]](#dist-518)
	* [**`get_point`** [#525]](#get_point-525)


&nbsp;

--------
# **Celegans**




&nbsp;
## **`__init__`** [#62]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L62) online

```python
def __init__(self, data_folder=None, base_dir=None, **kwargs):
```

&nbsp;  
docstring:

```text
This class handles loading and parsing neuroanatomical data for the C.
    elegans connectome from

https://www.biorxiv.org/content/10.1101/2020.04.30.066209v1

:param base_dir: path to directory to use for saving data (default
    value None)

:param kwargs: can be used to pass path to individual data folders.
    See brainrender/Utils/paths_manager.py

:param data_folder: str, path to a folder with data for the connectome
    # TODO replace with downloading data

```

&nbsp;
## **`_make_root`** [#84]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L84) online

```python
def _make_root(self, rootpath):
```

&nbsp;  
docstring:

```text
Creates a root mesh by merging the mesh corresponding to each neuron,

then saves it as an obj file at rootpath

```

&nbsp;
## **`get_neurons_by`** [#119]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L119) online

```python
def get_neurons_by(self, getby='pair', lookup=None):
```

&nbsp;  
docstring:

```text
Selects a subset of the neurons using some criteria and lookup key,

based on the neurons metadata

:param getby: str, name of the metadata key to use for selecting
    neurons

:param lookup: str/int.. neurons whose attribute 'getby' matches the
    lookup value will be selected

:returns: list of strings with neurons names

```

&nbsp;
## **`get_neuron_color`** [#151]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L151) online

```python
def get_neuron_color(self, neuron, colorby='type'):
```

&nbsp;  
docstring:

```text
Get a neuron's RGB color. Colors can be assigned based on different
    criteria

like the neuron's type or by individual neuron etc...

:param neuron: str, nueron name

:param colorby: str, metadata attribute to use for coloring

:returns: rgb values of color

```

&nbsp;
## **`_get_data`** [#186]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L186) online

```python
def _get_data(self):
```

&nbsp;  
docstring:

```text
Loads data and metadata for the C. elegans connectome.

```

&nbsp;
## **`_check_neuron_argument`** [#249]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L249) online

```python
def _check_neuron_argument(self, neurons):
```

&nbsp;  
docstring:

```text
Checks if a list of string includes neurons name, returns only

elements of the list that are correct names

:param neurons: list of strings with neurons names

```

&nbsp;
## **`_parse_neuron_skeleton`** [#272]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L272) online

```python
def _parse_neuron_skeleton(self, neuron):
```

&nbsp;  
docstring:

```text
Parses a neuron's skeleton information from skeleton .json file

to create a vtk actor that represents the neuron

:param neuron: str, neuron name

```

&nbsp;
## **`_get_structure_mesh`** [#308]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L308) online

```python
def _get_structure_mesh(self, acronym, **kwargs):
```

&nbsp;  
docstring:

```text
Get's the mesh for a brainregion, for this atlas it's just for

getting/making the root mesh

```

&nbsp;
## **`get_neurons`** [#329]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L329) online

```python
def get_neurons(self, neurons, alpha=1, as_skeleton=False,
    colorby='type'):
```

&nbsp;  
docstring:

```text
Renders neurons and adds returns to the scene.

:param neurons: list of names of neurons

:param alpha: float in range 0,1 -  neurons transparency

:param as_skeleton: bool (Default value = False), if True neurons are
    rendered as skeletons

otherwise as a full mesh showing the whole morphology

:param colorby: str, criteria to use to color the neurons. Accepts
    values like type, individual etc.

```

&nbsp;
## **`get_neurons_synapses`** [#371]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L371) online

```python
def get_neurons_synapses(self, scene_store, neurons, alpha=1,
    pre=False, post=False, colorby='synapse_type', draw_patches=False,
    draw_arrows=True):
```

&nbsp;  
docstring:

```text
THIS METHODS GETS CALLED BY SCENE, self referes to the instance of
    Scene not to this class.

Renders neurons and adds them to the scene.

:param neurons: list of names of neurons

:param alpha: float in range 0,1 -  neurons transparency

:param pre: bool, if True the presynaptic sites of each neuron are
    rendered

:param post: bool, if True the postsynaptic sites on each neuron are
    rendered

:param colorby: str, criteria to use to color the neurons.

 Accepts values like synapse_type, type, individual etc.

:param draw_patches: bool, default True. If true dark patches are used
    to show the location of post synapses

:param draw_arrows: bool, default True. If true arrows are used to
    show the location of post synapses

```

&nbsp;
## **`dist`** [#518]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L518) online

```python
def dist(p1, p2):
```

&nbsp;  
docstring:

no docstring

&nbsp;
## **`get_point`** [#525]
  
Check the [***``source code``***](https://github.com/brainglobe/brainrender/blob/master/brainrender/custom_atlases/celegans.py#L525) online

```python
def get_point(p1, p2, d, u):
```

&nbsp;  
docstring:

no docstring