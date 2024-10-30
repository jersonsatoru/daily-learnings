## Generate _N_ empty files

```bash
#!/bin/bash

grep '[a-z]*' /usr/share/dict/words \
    | shuf \
    | head -n2 \
    | xargs touch \
```