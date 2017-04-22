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
**view restartu verzi**
Rychlost neni dulezita (provadi se jen jednou pri deployi).

**Serad verze programu dle toho jak casto se restartovali v lednu 2017 (od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.282 | 14.044 | |
2 | 0.263 | 14.269 | |
3 | 0.262 | 14.640 | |
4 | 0.237 | 14.311 | |
5 | 0.259 | 14.329 | |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.250 | 14.816 | |
2 | 0.251 | 14.733 | |
3 | 0.245 | 14.832 | |
4 | 0.244 | 14.653 | |
5 | 0.246 | 14.533 | |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pivot table pro restarty programu | 0.274 ms | 15.123 s |  | 
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic) | 0.232 ms | 0.093 ms |  | 
Kolikrat se celkem kazda verze restartovala | 0.066 ms | 0.06 ms |  | 
 
 # Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic) | 0.26 ms | 14.319 s |  | 
Kolikrat se celkem kazda verze restartovala | 0.247 ms | 14.713 s |  | 
