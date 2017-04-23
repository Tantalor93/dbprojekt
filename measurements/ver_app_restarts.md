# OLAP
**Pivot table pro restarty programu**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.255 | 15048  | 4.507 | 22396.428 |
2 | 0.256 | 15081  | 0.346 | 22226.995 |
3 | 0.275 | 15333  | 0.344 | 21739.096 |
4 | 0.259 | 15002  | 0.348 | 21852.374 |
5 | 0.326 | 15152 | 0.346 | 23164.299 |

**Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.404 | 0.094  | 0.569 | 0.106 |
2 | 0.511 | 0.096 | 0.070 | 0.103 |
3 | 0.077 | 0.095 | 0.070 | 0.102 |
4 | 0.075 | 0.084 | 0.080 | 0.103 |
5 | 0.095 | 0.099 | 0.070 | 0.101 |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.057 | 0.055 | 0.042 | 0.075 |
2 | 0.090 | 0.074 | 0.042 | 0.074 |
3 | 0.071 | 0.063 | 0.041 | 0.073 |
4 | 0.061 | 0.057 | 0.042 | 0.073 |
5 | 0.054 | 0.052 | 0.043 | 0.078 |

# normal varianta

**Serad verze programu dle toho jak casto se restartovali v lednu 2017 (od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.282 | 14044 | 0.216 | 21525.095 |
2 | 0.263 | 14269 | 0.352 | 21316.021 |
3 | 0.262 | 14640 | 0.360 | 21408.937 |
4 | 0.237 | 14311 | 0.359 | 20915.267 |
5 | 0.259 | 14329 | 0.358 | 20679.772 |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.250 | 14.816 | 0.342 | 21943.105 |
2 | 0.251 | 14.733 | 0.346 | 21816.561 |
3 | 0.245 | 14.832 | 0.336 | 22018.110 |
4 | 0.244 | 14.653 | 0.334 | 21779.951 |
5 | 0.246 | 14.533 | 0.335 | 22745.693 |

# normal varianta s indexy

index nad app_run_time

**Serad verze programu dle toho jak casto se restartovali v lednu 2017 (od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |       |       |   0.527    |     18015.174      |
2 |       |       |   0.530    |     18202.813      |
3 |       |       |   0.559    |     18262.275     |
4 |       |       |    0.526   |     18737.569      |
5 |       |       |   0.532    |     17937.632     |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 |       |       |   0.509    |     20201.882      |
2 |       |       |    0.503   |      20522.129     |
3 |       |       |   0.506    |     19580.030      |
4 |       |       |    0.518    |     19242.078      |
5 |       |       |   0.512    |      19787.232     |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pivot table pro restarty programu | 0.274 ms | 15123 ms | 1.1782 ms | 22275.8384 ms | 
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic) | 0.232 ms | 0.093 ms | 0.1718 ms  | 0.103 ms | 
Kolikrat se celkem kazda verze restartovala | 0.066 ms | 0.06 ms | 0.042 ms | 0.0746 ms | 
 
 # Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic) | 0.26 ms | 14319 ms | 0.329 ms | 21169.0184 ms | 
Kolikrat se celkem kazda verze restartovala | 0.247 ms | 14713 ms | 0.3386 ms | 22060.684 ms |

 # Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic) | |  | 0.5348 ms|18231.0926 ms | 
Kolikrat se celkem kazda verze restartovala |  |  | 0.5096 ms | 19866.6702 ms |
