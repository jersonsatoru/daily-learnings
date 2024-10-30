## Generate N files with random name and random stuff

### Pre-requisites

- install __pwgen__ ```sudo apt install pwgen```

```bash
#!/bin/bash

yes 'shuf -n $RANDOM -o $(pwgen -N1 10).txt /usr/share/dict/words' \
    | head -n3 \
    | bash

```