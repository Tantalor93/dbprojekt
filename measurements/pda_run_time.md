# OLAP
**Vytvoreni pivot table**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 308 | 22987 | 0.971 | 21733.914 |
2 | 288 | 20940 | 2.908 | 21860.552 | 
3 | 285 | 19452 | 1.505 | 20881.166 |
4 | 279 | 19506 | 1.541 | 21690.422 |
5 | 261 | 19276 | 1.701 | 25135.042 |

**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.206 | 1.146 | 0.319 | 1.112 |
2 | 0.328 | 0.975 | 0.043 | 1.944 |
3 | 0.070 | 0.960 | 0.042 | 1.978 |
4 | 0.056 | 0.964 | 0.043 | 1.976 |
5 | 0.057 | 0.985 | 0.044 | 1.997 |

# Normal
**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.286 | 20217 | 1.363 | 21616.873 |
2 | 0.280 | 19554 | 1.249 | 20496.781 |
3 | 0.250 | 19071 | 1.306 | 20636.367 |
4 | 0.234 | 18847 | 1.790 | 20729.463 |
5 | 0.266 | 18681 | 1.318 | 20774.037 |

# Normal s indexy

**pro kazde zarizeni zjistit kolik hodin bylo pouzivano**

zde zadny index nepomohl

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Vytvoreni pivot table | 284.2 ms | 20432 ms | 1.7252 ms  | 22260.2192 ms |
pro kazde zarizeni zjistit kolik hodin bylo pouzivano | 0.143 ms | 1 ms | 0.0982 ms | 1.8014 ms |

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
pro kazde zarizeni zjistit kolik hodin bylo pouzivano | 0.263 ms | 19274 ms  | 1.4052 ms | 20822.787 ms |
