```
wc [text file] -- gives the lines, characters and words (wc -l,-c,-w)
wc -l *.pdb -- gives the .pdb files only
```
```
wc -l *.pdb > lengths.txt -- that will write the stuff on the windows.
```
```
sort -n lengths.txt -- sort the stuff in an order of number>>
```
echo hello > textfile1.txt -- open a file and write echo there
echo hello >> textfile2.txt -- everytime you write something it appends to this file
```
for loop
```
~/Desktop/data-shell/creatures$ for i in *.dat; do  echo $i  ; done
```

```
cagri@cakilic:~/Desktop/data-shell/creatures$ for i in *.dat; do  echo $i >> headers.txt  ; done
```
