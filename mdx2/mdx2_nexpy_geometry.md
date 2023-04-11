# Viewing the Geometry of your Experiment in NeXpy
## Adapted from the mdx2 tutorials of the erice 2022 data reduction workshop
NeXpy is the graphical user interface of mdx2 and allows the user to view geometry factors such as solid angle as well as generated reciprocal space plots etc.

To open NeXpy, run:
```
nexpy
```
in your terminal. This should open an app. 

Import the following dependencies:
```
import numpy as np

import matplotlib.pyplot as plt

import pandas as pd

from mdx2.utils import loadobj #important for loading nexus format files
```

