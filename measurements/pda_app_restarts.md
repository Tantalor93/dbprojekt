# OLAP
**Pivot table pro restarty programu**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.847 | 28270.167 |
2 |  |  | 0.346 | 28293.124 |
3 |  |  | 0.213 | 31139.352 |
4 |  |  | 0.305 | 27388.545 |
5 |  |  | 0.210 | 26809.321 |

**TOP 10 zarizeni, ktere se restartovali v lednu 2017** 

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 2.174 | 1.577 |
2 |  |  | 0.058 | 1.669 |
3 |  |  | 0.077 | 2.832 |
4 |  |  | 0.052 | 1.551 |
5 |  |  | 0.067 | 2.395 |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.062 | 4.321 |
2 |  |  | 0.043 | 2.866 |
3 |  |  | 0.030 | 1.247 |
4 |  |  | 0.043 | 2.115 |
5 |  |  | 0.032 | 1.497 |

# Normal varianta

**TOP 10 zarizeni, ktere se restartovali v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.244	| 24332.210 |
2 |  |  | 0.208 | 25419.327 |
3 |  |  | 0.377 | 26453.887 |
4 |  |  | 0.212 | 26395.068 |
5 |  |  | 0.367 | 24600.540 |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.215 | 23326.126 |
2 |  |  | 0.192 | 26031.301 |
3 |  |  | 0.348 | 27227.251 |
4 |  |  | 0.335 | 26522.748 |
5 |  |  | 0.337 | 26154.235 |

# Normal varianta s indexy

jediny index, ktery se zda, ze ovlivni rychlost je index nad *app_run_time*.

**TOP 10 zarizeni, ktere se restartovali v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.406	| 18923.428 |
2 |  |  | 0.550 | 19503.721 |
3 |  |  | 0.538 | 18428.466 |
4 |  |  | 0.536 | 18962.741 |
5 |  |  | 0.535 | 19025.467 |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.502  | 19752.007 |
2 |  |  | 0.504  | 19813.704 |
3 |  |  | 0.505 | 19945.740 |
4 |  |  | 0.504 | 19560.724 |
5 |  |  | 0.502 | 19075.938 |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pivot table pro restarty programu | | | 0.3842 ms | 28380.1018 ms |
TOP 10 zarizeni, ktere se restartovali v lednu 2017 | |  | 0.4856 ms | 2.0048 ms |
Kolikrat se celkem kazde zarizeni restartovalo |  |  | 0.042 ms | 2.4092 ms |

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
TOP 10 zarizeni, ktere se restartovali v lednu 2017 |  |  | 0.2816 ms | 25440.2064 ms | 
Kolikrat se celkem kazde zarizeni restartovalo |  |  | 0.2854 ms | 25852.3322 ms | 

# Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
TOP 10 zarizeni, ktere se restartovali v lednu 2017 |  |  | 0.513 ms | 18968.7646 ms | 
Kolikrat se celkem kazde zarizeni restartovalo |  |  | 0.5034 ms | 19629.6226 ms | 
