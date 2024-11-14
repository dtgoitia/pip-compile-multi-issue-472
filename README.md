**NOTE**: the last commit contains the correct usage of `pip-compile-build`. See previous commits to reproduce issue.

---

This works:

```
docker compose run --rm dependency-builder \
    pip-compile-multi \
        --backtracking \
        --strip-extras \
        --autoresolve \
        --live
```
