# SIMULATIONS
Repository of simulations with descriptions compatible with IMPEx-SPASE

## How to describe a simulation

Use your favorite editor to build what we call an impex tree, an XML file containing all the metadata related to the simulation outputs.

You can use [this file](https://github.com/CDPP-IRAP/SIMULATIONS/blob/master/trees/BT_Tree4.xml) as template.

## Contents of an IMPEx Tree

A tree must contain at least four resources: SimulationModel, SimulationRun, NumericalOutput and Granule. 

Respository is optional.

A unique ResourceID is assigned to each resource. Be careful with these ResourceID, because they are used by the tools (e.g. 3Dview) to build their user interface.

### SimulationModel

This resource gives information related to the code used for the simulation

### SimulationRun

This resource gives information related to an execution of the code with specific parameters

### NumericalOutput

This resource gives information related to the outputs of a specific run , i.e the description of each physical parameter

### Granule

This resource gives information related to each file containing a set of parameters described in NumericalOutput. For time series, a NumericalOutput points to several granules with the same caracteristics,except time.

### Naming Rules

#### SimulationModel 

spase://IMPEx/SimulationModel/IRAP/__*model*__

#### SimulationRun

spase://IMPEx/SimulationRun/IRAP/__*model*/*run*__

#### NumericalOutput

spase://IMPEx/NumericalOutput/IRAP/__*model*/*run*/*numericalOutput*__

#### Granule

spase://IMPEx/Granule/IRAP/__*model*/*run*/*numericalOutput*/*granule*__

## Example

spase://IMPEX/SimulationModel/IRAP/CPEMv2

spase://IMPEx/SimulationRun/IRAP/CPEMv2/test1

spase://IMPEx/NumericalOutput/IRAP/CPEMv2/test1/plasma_density

spase://IMPEx/Granule/IRAP/CPEMv2/test1/plasma_density/file

* In SimulationRun, ModelID must contain the ResourceID of SimulationModel
* In NumericalOutput, InputResourceID must contain the ResourceID of SimulationRun
* in Granule, parentID must contain the ResourceID of NumericalOutput

## URL of the associated data file

All the data files associated with an impex tree must be uploaded in the *data* directory, although you can alternatively use an external URL

If you want to use Github to store your data, write the URL of the datafile ( NetCDF ) in Granule/Source/URL

https://github.com/CDPP-IRAP/SIMULATIONS/blob/master/data/*name_of_your_data_file*?raw=true

Example:

https://github.com/CDPP-IRAP/SIMULATIONS/blob/master/data/charge_density_test_CPEMv2_7.nc?raw=

Be sure you enter the URL in the following way:
\<URL\>...\<URL\>

as 

\<URL\>

...

\<URL\> 

  will generate an error


## Where do you store your impex trees ?

Store your impex trees in the *trees* directory

## What is the URL of your impex tree

If you want to give access to your tree (e.g. to 3DView) use the following URL:

https://raw.githubusercontent.com/CDPP-IRAP/SIMULATIONS/master/trees/*name_of_your_tree*

