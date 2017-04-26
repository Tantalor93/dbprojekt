# OLAP
**Vytvoreni pivot table**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.971 | 21733.914 |
2 |  |  | 2.908 | 21860.552 | 
3 |  |  | 1.505 | 20881.166 |
4 |  |  | 1.541 | 21690.422 |
5 |  |  | 1.701 | 25135.042 |

**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 0.319 | 1.112 |
2 |  |  | 0.043 | 1.944 |
3 |  |  | 0.042 | 1.978 |
4 |  |  | 0.043 | 1.976 |
5 |  |  | 0.044 | 1.997 |

# Normal
**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 |  |  | 1.363 | 21616.873 |
2 |  |  | 1.249 | 20496.781 |
3 |  |  | 1.306 | 20636.367 |
4 |  |  | 1.790 | 20729.463 |
5 |  |  | 1.318 | 20774.037 |

# Normal s indexy

**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

zde zadny index nepomohl

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Vytvoreni pivot table | | | 1.7252 ms  | 22260.2192 ms |
pro kazde zarizeni zjistit kolik hodin bylo pouzivano | | | 0.0982 ms | 1.8014 ms |

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
pro kazde zarizeni zjistit kolik hodin bylo pouzivano |  |   | 1.4052 ms | 20822.787 ms |
