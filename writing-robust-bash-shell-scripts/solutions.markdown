1. `set -o nounset` or `set -u`
2. `set -o errexit` or `set -e`; `command || true`
3. `set -o pipefail`
4. `mkdir -p dir` or `mkdir --parents dir`
5. `rm -f file`
6. `if [ "$hello" = "hello" ]`
7. `"$@"`
8. `trap "rm -rf $lockfile; exit" INT TERM EXIT`
9. Copy files first and move back. Move is atomic.
 1. Duplicate data
 2. Open file handlers. `lsof`
