## Exercise 1

## EXERCISE 2

1. Run the following command
```
curl https://en.wikipedia.org/wiki/List_of_cyberattacks > cyberattacks.txt
```

2. Use grep to extract all the lines that contain the keyword "meta"
```
cat cyberattacks.txt | grep meta
```

3. Now only extract "meta" and the first following word. You might use grep options to enable the use of regex (Regular Expressions)
```
cat cyberattacks.txt | grep -oP "meta\s\w+"
```

4. Only extract the follwing word (but not the keyword "meta")
```
cat cyberattacks.txt | grep -oP "(?<=meta\s)\w+"
```

5. Retrieve all titles from wikipedia page

  a. Try to run the following command
```
cat cyberattacks.txt | grep -P 'A cyberattack is'
```

  b.  Now try the following
```
cat cyberattacks.txt | grep -P 'A <a href="/wiki/Cyberattack" title="Cyberattack">cyberattack</a> is any type'
#Does not work if the text is modified 
```

  c.  Now try the following
```
cat cyberattacks.txt | grep -A1 'mw-content-text' | grep -v 'mw-content-text'
#it is not based on the text but on a tag (balise : <title>)

#other possibility ; stock the title in the file titlePatern.txt
cat cyberattacks.txt | grep -oP "(?<=<title>).*(?=</title>)" > titlePatern.txt
```

6. Extract the table title, make a list of cyber attacks based on section title
```
cat cyberattacks.txt | grep -oP "(?<=<title>).*(?=</title>)"

```
