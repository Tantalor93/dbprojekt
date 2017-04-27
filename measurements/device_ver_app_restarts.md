# OLAP
**Pivot table pro restarty programu**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.265 | 16160.68 | 0.376 | 21578.199 |
2 | 0.267 | 15874.541 | 0.377 | 20876.688 |
3 | 0.275 | 15579.786 | 0.386 | 21106.686 |
4 | 0.277 | 16250.45 | 0.375 | 21590.108 |

**Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (s) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.113 | 0.585 | 0.099 | 1.180 |
2 | 0.123 | 0.609 | 0.100 | 1.113 |
3 | 0.114 | 0.598 | 0.752 | 1.245 |
4 | 0.109 | 0.627 | 0.099 | 1.107 |

# normal varianta

**Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.319 | 15543.265 | 0.393 | 20363.304 |
2 | 0.283 | 15186.799 | 0.400 | 20864.075 |
3 | 0.305 | 15229.794 | 0.395 | 20379.065 |
4 | 0.306 | 15304.234 | 0.391 | 20449.423 |

# normal varianta s indexy

index nad app_run_time

**Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017**

Nr | PC-1 Planning time (ms) | PC-1 Execution time (ms) | PC-2 Planning time (ms) | PC-2 Execution time (ms) |
--- | ------------------ | ------------------ | --- | ---
1 | 0.361 | 14603.137 | 0.447 | 18947.593 |
2 | 0.384 | 14837.265 | 0.448 | 18892.459 |
3 | 0.352 | 14626.681 | 0.449 | 18373.732 |
4 | 0.341 | 14741.881 | 0.281 | 18333.301 |

# Prumerne vysledky OLAP

Prikaz | PC-1 Planning time (ms) | PC-1 Execution Time (ms) | PC-2 Planning time (ms) | PC-2 Execution Time (ms) |
--- | --- | --- | --- | ---
Pivot table pro restarty programu | 0.271 | 15959.61 | 0.3875 | 21287.92 
Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017 | 0.115 | 0.605 | 0.263 | 1.161

# Prumerne vysledky Normal

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017 | 0.303 | 15316.02 | 0.395 | 20513.967

 # Prumerne vysledky Normal s indexy

Prikaz | PC-1 Planning time | PC-1 Execution Time | PC-2 Planning time | PC-2 Execution Time |
--- | --- | --- | --- | ---
Ktery typ zarizeni s jakou verzi programu se nejcasteji restartoval v lednu 2017 | 0.36 | 14702.24 | 0.406 | 18636.771
