# OLAP
**Pivot table**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.585  | 45994.267 |
2 |  |  | 0.085 | 46967.079 |
3 |  |  | 0.085  | 46258.447 |
4 |  |  | 0.084 | 46135.095 |

**Celkovy pocet ruznych zarizeni pro kazdou verzi** 

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.444 | 0.129 |
2 |  |  | 0.032 | 0.071  |
3 |  |  | 0.043 | 0.119 |
4 |  |  | 0.043 | 0.118 |

**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.071 | 0.135  |
2 |  |  | 0.072 | 0.137 |
3 |  |  | 0.049 | 0.135 |
4 |  |  | 0.072 | 0.083 |

# Normal varianta

**Celkovy pocet ruznych zarizeni pro kazdou verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.048 | 13225.377 |
2 |  |  | 0.050 | 12888.842 |
3 |  |  | 0.052 | 12679.688 |
4 |  |  | 0.048 | 13942.458 |

**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.077 | 15028.583 |
2 |  |  | 0.078 | 14839.978 |
3 |  |  | 0.080 | 14408.162 |
4 |  |  | 0.079 | 15259.401 |

# Normal varianta s indexy

indexy nad program_ver a funkcionalni indexy nad DATE_PART('YEAR',time) a DATE_PART('MONTH',time)

**Celkovy pocet ruznych zarizeni pro kazdou verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.100 | 7996.412 |
2 |  |  | 0.099 | 8009.561 |
3 |  |  | 0.102 | 7273.558 |
4 |  |  | 0.101 | 7327.604 |


**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.205 | 12867.493 |
2 |  |  | 0.210 | 12358.442 |
3 |  |  | 0.209 | 11521.614 |
4 |  |  | 0.216 | 11533.877 |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
pivot table | | | 0.20975 ms | 46338.722 ms |
Celkovy pocet ruznych zarizeni pro kazdou verzi | | | 0.1405 ms | 0.10925 ms |
Pocet ruznych zarizeni v lednu 2017 | | | 0.066 ms | 0.1225 ms |

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Celkovy pocet ruznych zarizeni pro kazdou verzi | | | 0.0495 ms | 13184.09125 ms |
Pocet ruznych zarizeni v lednu 2017 | | | 0.0785 ms | 14884.031 ms |


# Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Celkovy pocet ruznych zarizeni pro kazdou verzi | | | 0.1005 ms | 7651.78375 ms |
Pocet ruznych zarizeni v lednu 2017 | | | 0.21 ms | 12070.3565 ms |
