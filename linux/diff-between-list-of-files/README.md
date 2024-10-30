## Diff between list of files

In this case, we need that each *.png must have its counterpart *.txt (image description), so:

_Obs.: you should first enter in the __linux/diff-between-list-of-files__ directory first to run the code_


```bash
#!/bin/bash

bash -c "diff <(ls sample/*.jpg | sed -e 's/\.[^.]*$//') <(ls sample/*.txt | sed -e 's/\.[^.]*$//')" \
    | grep "^[<>]" \
    | awk '/^</{print $2 ".jpg"} /^>/{print $2 ".txt"}'

# in my case, 'bash -c' was necessary, for some reason, my diff commando was returning an error (diff: /proc/self/blabla - file or directory not found)
```

There's another way to achieve the same result, as follows:

```bash
#!/bin/bash


 ls sample/*.(jpg|txt) \
    | sed -e 's/\.[^.]*$//' \
    | uniq -c \
    | awk '/^\s*1 /{print $2 "*"}'

```
