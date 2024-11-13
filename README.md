To reproduce the issue, clone the repo, and at the root of the repo run:

```
docker compose run --rm dependency-builder \
    pip-compile-multi \
        --backtracking \
        --strip-extras \
        --live
```
