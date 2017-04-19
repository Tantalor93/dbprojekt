# OLAP
**Pivot table pro restarty programu**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.246 | 16.014 | |
2 | 0.305 | 15.845 | |
3 | 0.456 | 16.645 | |
4 | 0.311 | 17.155 | |
5 | 0.309 | 16.550 | |

**TOP 10 zarizeni, ktere se restartovali v lednu 2017** 

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.479 | 1.573 | |
2 | 0.088 | 1.520 | |
3 | 0.075 | 1.385 | |
4 | 0.091 | 1.479 | |
5 | 0.095 | 1.387 | |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.047 | 1.042 | |
2 | 0.054 | 1.030 | |
3 | 0.052 | 1.033 | |
4 | 0.058 | 1.131 | |
5 | 0.056 | 1.032 | |

# Normal s materializovanymi pohledy
**tabulka restartu zarizeni (vsechny restarty vsech zarizeni, nic neni agregovano)**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (s) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.899 | 17.417 | |
2 | 0.231 | 16.223 | |
3 | 0.302 | 15.273 | |
4 | 0.236 | 15.620 | |
5 | 0.292 | 15.766 | |

**TOP 10 zarizeni, ktere se restartovali v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.445 | 38.945 | |
2 | 0.085 | 39.287 | |
3 | 0.081 | 37.556 | |
4 | 0.095 | 38.187 | |
5 | 0.091 | 38.652 | |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.070 | 3.611 | |
2 | 0.066 | 3.678 | |
3 | 0.061 | 3.561 | |
4 | 0.062 | 3.554 | |
5 | 0.062 | 3.528 | |

# Normal bez materializovanych pohledu

**TOP 10 zarizeni, ktere se restartovali v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.244 | 24332.210 |

**Kolikrat se celkem kazde zarizeni restartovalo**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.215 | 23326.126 |


# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pivot table pro restarty programu | 0.325 ms | 16.442 s |  | 
TOP 10 zarizeni, ktere se restartovali v lednu 2017 | 0.166 ms | 1.469 ms | | 
Kolikrat se celkem kazde zarizeni restartovalo | 0.053 ms | 1.054 ms | |

# Prumerne vysledky Normal s materializovanymi pohledy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
tabulka restartu zarizeni (vsechny restarty vsech zarizeni, nic neni agregovano) | 0.392 ms | 16.060 s | |
TOP 10 zarizeni, ktere se restartovali v lednu 2017 | 0.159 ms | 38.525 ms | | 
Kolikrat se celkem kazde zarizeni restartovalo | 0.064 ms | 3.586 ms | | 
