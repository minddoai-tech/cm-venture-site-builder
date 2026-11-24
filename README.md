# MindDo venture phone-site builder

This public repository builds the web version of student Expo projects for `cm-venture-sites`.

The hosting service dispatches `build-phone-site.yml` with a public student repository, an exact commit, and a DNS-safe site slug. The workflow has two jobs:

1. `build` has no repository permissions and receives no secrets. It downloads the exact public commit, installs the project, and runs `npx expo export -p web`.
2. `publish` receives only the built artifact. It writes that output and `.site-build.json` to `site/<slug>`.

Student code never runs in the hosting service or in a job with write access. A failed build leaves the previous successful branch unchanged.

Keep this repository public so GitHub-hosted runner usage follows the public-repository allowance.
