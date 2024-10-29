## Renaming files using sed

We want to add a new chapter between chapter 3 and chapter 4 so...:

_Obs. Should be executed on the linux/renaming-files/using-sed directory_

```bash
#!/bin/bash

paste \
    <(seq 3 8 | sed -e 's/\(.*\)/files\/chapter\1.txt/') \
    <(seq 4 9 | sed "s/\(.*\)/result-generated\/chapter\1.txt/") \
    | sed "s/\(.*\)/mv \1/" \
    | bash
```


To revert the changes, run:

```bash
#!/bin/bash

paste \
    <(seq 4 9 | sed "s/\(.*\)/result-generated\/chapter\1.txt/") \
    <(seq 3 8 | sed "s/\(.*\)/files\/chapter\1.txt/") \
    | sed "s/\(.*\)/mv \1/" \
    | bash
```