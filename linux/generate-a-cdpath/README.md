## Generating a CDPATH in your Ubuntu

```bash
#!/bin/bash

echo 'CDPATH=$HOME' \
        $(cd && ls -d */ | sed -e 's@^@$HOME/@' -e 's@/$@@') \
        .. \
        | tr " " :

```