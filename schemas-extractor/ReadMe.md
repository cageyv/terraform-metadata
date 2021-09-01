Simple utility to get schemas of all official Terraform Providers

How to Use
-----

1. Ensure you have `GOPATH` env variable set up

2. Run `make`

3. You'll see `schemas` directory with schemas and 'failure.txt' file with list of failed providers

4. Copy all json files from `schemas` directory to `/REPO_ROOT/terraform/model/providers/`
5. Copy providers.list to `/REPO_ROOT/terraform/model/`


Flags and Parameters
---------
### Filtering
- To filter providers:
  - `make providers ONLY="aws cloudflare"`
- To filter provisioners:
  - `make provisioners ONLY="local-exec file"`
- To filter backends:
  - `make backends ONLY="consul atlas"`

### Environment Variables - General
- `UPDATE_SKIP=1` - This skips the Git update process for all repositories (See ~line 45 in common.sh)
- `UPDATE_PARALLEL=1` - Causes the update_or_clone function to be called in parrallel via & (See ~Line 70 in common.sh)
- `GENERATE_PARALLEL=1` - Causes the schema generation to be called in parralel via & (See ~line 157 in build-providers.sh for example)
- `RESET_REPOS=1` - Script will force a git reset and git clean on the repository if it is not clear

### Environment Variables - CI script only
- `KILL_CPU=1` - Causes the schema generation to run in parrallel via &. Same as `GENERATE_PARALLEL` above.
