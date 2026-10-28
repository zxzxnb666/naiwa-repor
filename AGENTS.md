# Repository maintenance

This workspace publishes the APT source at https://zxzxnb666.github.io/naiwa-repor/.
The display name is 奶蛙爱好者源; keep the repository identifier `naiwa-repor`.

Put existing release packages in debs/ without changing already published package bytes or versions. CydiaIcon.png is the user's source icon migrated from the old mango workspace.

Build on Debian/Ubuntu with apt-ftparchive (apt-utils), xz and optionally qrencode installed:

```sh
REPOSITORY_NAME=naiwa-repor REPOSITORY_OWNER=zxzxnb666 SOURCE_URL=https://zxzxnb666.github.io/naiwa-repor/ bash scripts/update-repository.sh
```

Output is _site/; never commit generated Packages, Release or _site/. GitHub Actions runs this build and deploys Pages on a push to main. On this iPhone, apt-ftparchive and xz are unavailable: check script syntax with `bash -n scripts/update-repository.sh`, inspect each package with `dpkg-deb -f` and `dpkg-deb -c`, and check file integrity with `sha256sum`. The full index build must run in Actions. There is no local executable app to launch or install for this repository.

Use Apelin git tools to commit and push only when publication is requested. The old mango workspace has a divergent history; do not merge it or change this workspace's origin to it.
