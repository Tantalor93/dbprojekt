# OLAP
**Pivot table**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.087 | 69247.386 | 0.585  | 45994.267 |
2 | 0.089 | 65955.164 | 0.085 | 46967.079 |
3 | 0.099 | 66156.792 | 0.085  | 46258.447 |
4 | 0.095 | 66692.572 | 0.084 | 46135.095 |

**Celkovy pocet ruznych zarizeni pro kazdou verzi** 

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.290 | 0.088 | 0.444 | 0.129 |
2 | 0.052 | 0.074 | 0.032 | 0.071  |
3 | 0.304 | 0.078 | 0.043 | 0.119 |
4 | 0.059 | 0.077 | 0.043 | 0.118 |

**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.094 | 0.094 | 0.071 | 0.135  |
2 | 0.079 | 0.090 | 0.072 | 0.137 |
3 | 0.071 | 0.080 | 0.049 | 0.135 |
4 | 0.071 | 0.092 | 0.072 | 0.083 |

# Normal varianta

**Celkovy pocet ruznych zarizeni pro kazdou verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.064 | 18396.625 | 0.048 | 13225.377 |
2 | 0.075 | 17879.980 | 0.050 | 12888.842 |
3 | 0.057 | 18076.093 | 0.052 | 12679.688 |
4 | 0.063 | 18337.579 | 0.048 | 13942.458 |

**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.092 | 18309.567 | 0.077 | 15028.583 |
2 | 0.077 | 18266.916 | 0.078 | 14839.978 |
3 | 0.087 | 18450.810 | 0.080 | 14408.162 |
4 | 0.091 | 18004.400 | 0.079 | 15259.401 |

# Normal varianta s indexy

indexy nad program_ver a time

**Celkovy pocet ruznych zarizeni pro kazdou verzi**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.080 | 14639.288 | 0.100 | 7996.412 |
2 | 0.082 | 14632.650 | 0.099 | 8009.561 |
3 | 0.092 | 14167.782 | 0.102 | 7273.558 |
4 | 0.080 | 14682.949 | 0.101 | 7327.604 |


**Pocet ruznych zarizeni v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.110 | 14704.673 | 0.205 | 12867.493 |
2 | 0.094 | 14777.995 | 0.210 | 12358.442 |
3 | 0.122 | 14857.157 | 0.209 | 11521.614 |
4 | 0.123 | 14852.624 | 0.216 | 11533.877 |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
pivot table | 0.0925 ms | 67012.9785 ms | 0.20975 ms | 46338.722 ms |
Celkovy pocet ruznych zarizeni pro kazdou verzi | 0.17625 ms | 0.07925 ms | 0.1405 ms | 0.10925 ms |
Pocet ruznych zarizeni v lednu 2017 | 0.07875 ms | 0.089 ms | 0.066 ms | 0.1225 ms |

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Celkovy pocet ruznych zarizeni pro kazdou verzi | 0.17625 ms | 18172.56925 ms | 0.0495 ms | 13184.09125 ms |
Pocet ruznych zarizeni v lednu 2017 | 0.08675 ms | 18257.92325 ms | 0.0785 ms | 14884.031 ms |


# Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Celkovy pocet ruznych zarizeni pro kazdou verzi | 0.0835 ms | 14530.66725 ms | 0.1005 ms | 7651.78375 ms |
Pocet ruznych zarizeni v lednu 2017 | 0.11225 ms | 14798.11225 ms | 0.21 ms | 12070.3565 ms |
