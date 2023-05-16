# Sagemath

[SageMath](https://doc.sagemath.org/html/en/index.html) is a computer algebra system (CAS) with features covering many aspects of mathematics, including algebra, combinatorics, graph theory, numerical analysis, number theory, calculus and statistics. 

Install the package:

    sudo apt install sagemath

Check you can [use it in your python virtual environment](https://pypi.org/project/sagemath/):

    pip install sagemath

For writing stand-alone Python scripts that use the Sage library:

```text
#!/usr/bin/env sage

import sys
from sage.all import *

if len(sys.argv) != 2:
    print("Usage: %s <n>" % sys.argv[0])
    print("Outputs the prime factorization of n.")
    sys.exit(1)

print(factor(sage_eval(sys.argv[1])))
```

## Troubleshooting

`SAGE_ROOT` must be in your `PATH`.

