# Summary

This is a repo for reporting compatibility issue in `lint-staged` with git sparse checkout feature.

# Step to reproduce the issue

```sh
# clone this repo with git sparse feature
git clone --sparse git@github.com:chengcyber/lint-staged-sparse-issue.git

# go to the repo folder
cd lint-staged-sparse-issue

# sparse checkout for app1
git sparse-checkout add apps/app1

# ... real develop for app1 ...
touch apps/app1/a.txt
git add apps/app1/a.txt

# Run lint-staged
npx lint-staged
```

However, `npx lint-staged` complains:

```sh
npx lint-staged
[Error: ENOENT: no such file or directory, open '/private/tmp/lint-staged-sparse-issue/apps/app2/package.json'] {
  errno: -2,
  code: 'ENOENT',
  syscall: 'open',
  path: '/private/tmp/lint-staged-sparse-issue/apps/app2/package.json'
}
✖ No valid configuration found.
```