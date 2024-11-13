To reproduce the issue, clone the repo, and at the root of the repo run:

```
docker compose run --rm dependency-builder \
    pip-compile-multi \
        --backtracking \
        --strip-extras \
        --live
```

You should get this error:

```
Package boto3 was resolved to different versions in different environments: 1.35.7 and 1.35.59
Traceback (most recent call last):
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/cli_v1.py", line 26, in cli
    recompile()
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/actions.py", line 31, in recompile
    compile_topologically(env_confs, deduplicator)
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/actions.py", line 38, in compile_topologically
    if env.maybe_create_lockfile():
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/environment.py", line 51, in maybe_create_lockfile
    self.create_lockfile()
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/environment.py", line 72, in create_lockfile
    self.fix_lockfile()
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/environment.py", line 134, in fix_lockfile
    sections = [
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/environment.py", line 135, in <listcomp>
    self.fix_pin(section)
  File "/usr/local/lib/python3.10/site-packages/pipcompilemulti/environment.py", line 211, in fix_pin
    raise RuntimeError(
RuntimeError: Please add constraints for the package version listed above
```
