# OLAP
**Pivot table**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.068 | 18133.632 | 0.082 | 22186.685 |
2 | 0.099 | 18259.197 | 0.078 | 21475.563 |
3 | 0.085 | 18019.045 | 0.081 | 21505.578 |
4 | 0.081 | 18120.155 | 0.079 | 22819.644 |

**Pocet spojeni celkem pro kazdou verzi** 

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.310 | 0.074 | 0.086 | 0.169 |
2 | 0.066 | 0.078 | 0.746 | 0.188 |
3 | 0.075 | 0.102 | 0.040 | 0.120 |
4 | 0.051 | 0.075 | 0.041 | 0.118 |

**Pocet spojeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.078 | 0.085 | 0.075 | 0.136 |
2 | 0.077 | 0.086 | 0.077 | 0.138 |
3 | 0.069 | 0.086 | 0.099 | 0.165 |
4 | 0.078 | 0.092 | 0.072 | 0.133 |

# Normal varianta

**Celkovy pocet spojeni pro kazdou verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.064 | 1204.423 | 0.047 | 1503.792 |
2 | 0.067 | 1193.151 | 0.048 | 1495.824 |
3 | 0.065 | 1214.479 | 0.046 | 1489.830 |
4 | 0.061 | 1218.344 | 0.047 | 1501.052 |

**Pocet spojeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.088 | 8652.474 | 0.074 | 3643.593 |
2 | 0.089 | 8358.984 | 0.073 | 4235.274 |
3 | 0.108 | 8395.901 | 0.077 | 3633.736 |
4 | 0.085 | 8350.257 | 0.075 | 3624.846 |


# Normal varianta s indexy

pouziti indexu nad time v tabulce conn_log

**Celkovy pocet spojeni pro kazdou verzi**

stejne jak normal varianta 


**Pocet spojeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.241 | 1967.429 |
2 |  |  | 0.125 | 1959.028 |
3 |  |  | 0.205 | 1980.402 |
4 |  |  | 0.208 | 1968.766 |


# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pivot table | 0.08325 ms | 18133.01 ms | 0.08 ms | 21996.8675 ms |
Pocet spojeni celkem pro kazdou verzi | 0.1255 ms | 0.08225 ms | 0.041 ms | 0.14875 ms |
Pocet spojeni v lednu 2017 | 0.0755 ms | 0.08725 ms | 0.08075 ms | 0.143 ms |


# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Celkovy pocet spojeni pro kazdou verzi | 0.06425 ms | 1207.59925 ms | 0.047 ms | 1497.6245 ms |
Pocet spojeni v lednu 2017 | 0.0925 ms | 8439.404 ms | 0.07475 ms | 3784.36225 ms |

# Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Pocet spojeni v lednu 2017 | | | 0.19475 ms | 1968.90625 ms |
