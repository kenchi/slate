# Kenchi-specific instructions

## To update to upstream commit hash

1. Make sure you're not on a -kenchi version anywhere, it makes workspaces sad (e.g. you'll probably want to do `git reset --hard HEAD^` if the latest commit is a version change)
1. `git fetch && git rebase -i UPSTREAMHASH`
1. Resolve any issues

## To apply a patch

1. Make sure you're not on a -kenchi version anywhere, it makes workspaces sad (e.g. you'll probably want to do `git reset --hard HEAD^` if the latest commit is a version change)
1. Apply the patch

## To release after one of the above

1. `yarn`
1. If you want to be extra safe, make sure `node_modules/slate*` is a symlink to the appropriate `packages/` dir
1. `yarn prerelease` (make sure succeeds)
1. `git push -f`
1. `yarn lerna release`
1. Choose `Choose version` and enter `0.##.#-kenchi.#`
1. Lerna will try to release but fail, this is OK
1. In every package.json, replace `"name": "slate` with `"name": "@kenchi/slate`
1. In every packages dir, run `npm publish`
1. `0.##.#-kenchi.#` is now available in our private Github packages
