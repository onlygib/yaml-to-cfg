### What it do
Takes a yaml file in, puts a cfg file out. Useful when you need to create a cfg file for local dev with a service, but the env is written in a yaml file elsewhere. Converting this manually is painful...

### How
1. Clone this repo
2. In repo root, install deps: `pip3 install --user -r requirements.txt`
3. Run the utility at the repo root: `python3 . [yaml-path] [target-path]`

### Example
I want to create a cfg file for accountentryservice using the latest yaml file in gcp-infrastructure-templates.
- yaml path: `~/code/edu/gcp-infrastructure-templates/apps/accountentryservice/staging/patch-deployment.yaml`
- cfg path:  `~/code/edu/accountentryservice/env/cfg/beta1.cfg`

To do this, in the repo root I run:
```
# Args are from above. First arg is yaml path, second arg is cfg path
python3 . \
  ~/code/edu/gcp-infrastructure-templates/apps/accountentryservice/staging/patch-deployment.yaml \
  ~/code/edu/accountentryservice/env/cfg/beta1.cfg
```

### Warnings and considerations
- If `target-path` arg is a file that already exists, it will be overwritten.
- If `target-path` arg is an existing directory, a file with name beta1.cfg will be created in that directory.

### Tip: Adding this tool to your path
In your .bashrc, add the following, changing the python3 binary name (if necessary) and path to the repo-root to match your system.
```
yaml-to-cfg() {
    python3 ~/code/tools/python/yaml-to-cfg "$@"
}
```
