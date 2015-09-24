# pyPixelClusterizer [![Build Status](https://travis-ci.org/SiLab-Bonn/pyPixelClusterizer.svg?branch=master)](https://travis-ci.org/SiLab-Bonn/pyPixelClusterizer) [![Build Status](https://ci.appveyor.com/api/projects/status/github/SiLab-Bonn/pyPixelClusterizer)](https://ci.appveyor.com/project/DavidLP/pyPixelClusterizer)

pyPixelClusterizer is an easy to use pixel hit-clusterizer for Python. It clusters hits on an event basis in space and time. 

The hits have to be a numpy recarray with data types as defined in data_struct.HitInfo. The fields are:
- event_number
- frame
- column
- row
- charge

Cluster information (data_struct.ClusterInfo) is created with the following fields:
- event_number
- ID
- size
- charge
- seed_column
- seed_row
- mean_column
- mean_row

Also cluster hit information (data_struct.ClusterHitInfo) is created. The cluster hit information is the hit information extended by the following fields:
- cluster_ID
- is_seed
- cluster_size
- n_cluster

# Installation

The stable code is hosted on PyPI and can be installed by typing:

pip install pyPixelClusterizer

# Usage

import numpy as np

from tables import dtype_from_descr

from pyPixelClusterizer.hit_clusterizer import HitClusterizer

from pyPixelClusterizer import data_struct

hits = np.ones(shape=(3, ), dtype=dtype_from_descr(data_struct.HitInfo))  # create some data

clusterizer = HitClusterizer()  # initialize clusterizer

clusterizer.add_hits(hits)  # cluster hits  # add hits to clusterizer

print (clusterizer.get_cluster())  # print cluster

print (clusterizer.get_hit_cluster())  # print hits + cluster info

Also take a look at the example folder!

