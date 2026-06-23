## Old 
```bash
if [ "$1" = "cp" ] && [ "$2" = "create" ]; then
    # ...
fi
```
## Latest:
```bash
if [[ "$1" == "cp" && "$2" == "create" ]]; then
    # ....
fi
```
same as :