1. open `regedit.exe`
2. in **HKEY_CLASSES_ROOT** create key **hifi**
3. in **hifi**:
4. _(default) = "URL:High Fidelity"_
5. _URL Protocol = ""_
6. create key in **hifi** with the name **DefaultIcon**
7. in **DefaultIcon**:
8. _(default) = "High Fidelity\Interface\interface.ico"_
9. create key in **hifi** with the name **shell**
10. create key in **shell** with the name **open**
11. create key in **open** with the name **command**
12. in **command**:
13. _(default) = " "....\interface.exe" -url "%1" "_