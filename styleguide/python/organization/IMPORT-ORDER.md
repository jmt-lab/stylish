---
type: Styleguide Rule
description: |-
  Group imports in three sections separated by blank lines:
  1. Standard library
  2. Third-party packages
  3. Local application/library imports
  Within each group, alphabetize. Use isort or ruff's import sorting
  (ruff check --select I --fix) to automate this. Configure the tool
  to be compatible with your formatter (e.g., Black).
language: python
category: organization
rule_id: IMPORT-ORDER
priority: warn
tags:
- imports
- formatting
- readability
- organization
---
Group imports in three sections separated by blank lines:
1. Standard library
2. Third-party packages
3. Local application/library imports
Within each group, alphabetize. Use isort or ruff's import sorting
(ruff check --select I --fix) to automate this. Configure the tool
to be compatible with your formatter (e.g., Black).

## Good

- import os
import sys

import numpy
import requests

from .entity import Entity
from .renderer import Renderer
- import os
import sys

from typing import List

import numpy as np

from myapp import utils


## Bad

- from .entity import Entity
import numpy
import os
- from myapp import utils
import numpy as np
import sys
from typing import List
import os

