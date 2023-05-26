https://underthewire.tech/century-1

0 -> 1
```
ssh Century1@century.underthewire.tech 
```
```
century1
```

1 -> 2
```
$psbuildversion
```
```
10.0.14393.5127
```

2 -> 3
```
get-command wget
```
```
invoke-webrequest443
```

3 -> 4
```
(Get-ChildItem | measure).count
```
```
123
```

4 -> 5
```
get-content
```
```
49125
```

5 -> 6
```
get-addomain
```
```
underthewire3347
```

6 -> 7
```
dir
```
```
197
```

7 -> 8
```
dir -r
```
```
7points
```

8 -> 9
```
(get-content .\unique.txt | get-unique | measure).count
```
```
696
```

9 -> 10
```
(Get-Content .\Word_File.txt | Select-String -Pattern "([a-zA-Z'-]+)" -AllMatches).Matches.Value[160]
```
```
pierid
nonapplicabness
patinas
```