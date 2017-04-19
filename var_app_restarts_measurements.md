# OLAP
**Pivot table pro restarty programu**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.255 | 15.048  | |
2 | 0.256 | 15.081  | |
3 | 0.275 | 15.333  | |
4 | 0.259 | 15.002 | |
5 | 0.326 | 15.152 | |

**Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.404 | 0.094  | |
2 | 0.511 | 0.096 | |
3 | 0.077 | 0.095 | |
4 | 0.075 | 0.084 | |
5 | 0.095 | 0.099  | |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.057 | 0.055 | |
2 | 0.090 | 0.074 | |
3 | 0.071 | 0.063 | |
4 | 0.061 | 0.057 | |
5 | 0.054 | 0.052 | |

# Normal
**tabulka restartu verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.261 | 15.492 | |
2 | 0.222 | 15.362 | |
3 | 0.257 | 15.479 | |
4 | 0.230 | 15.382 | |
5 | 0.367 | 15.026 | |

**Serad verze programu dle toho jak casto se restartovali v lednu 2017 (od nejmin restartu po nejvic)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.328 | 11.844 | |
2 | 0.092 | 11.762 | |
3 | 0.079 | 12.15 | |
4 | 0.077 | 11.898 | |
5 | 0.077 | 11.594 | |

**Kolikrat se celkem kazda verze restartovala**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (,s) | PC-2 Planning time (ms) | PC-2 Execution time (,s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.071 | 3.197 | |
2 | 0.061 | 3.052 | |
3 | 0.061 | 3.126 | |
4 | 0.076 | 2.862 | |
5 | 0.060 | 2.946 | |

# normal varianta bez materializovanych pohledu
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
Pivot table pro restarty programu |  | |  | 
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic)* |  | |  | 
Kolikrat se celkem kazda verze restartovala |  | |  | 

# Prumerne vysledky Normal s materialized view

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
tabulka restartu verzi |  | |  | 
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic)* |  | |  | 
Kolikrat se celkem kazda verze restartovala |  | |  | 
 
 # Prumerne vysledky Normal s beznym view

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Serad verze programu dle toho jak casto se restartovali v lednu 2017(od nejmin restartu po nejvic)* |  | |  | 
Kolikrat se celkem kazda verze restartovala |  | |  | 
