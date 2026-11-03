# Source and review

Learned on 2026-11-01 from the public GitHub repository `anthropics/skills` at commit ca45fc496a3436251f191354091d557da31c15b5, folder `skills/web-artifacts-builder`.

The skill body was installed with its frontmatter metadata moved into `skill.yaml`, plus a short Muse adaptation section added at the end. The scripts and the shadcn components tarball are the upstream files, used under the Apache License 2.0, and the upstream LICENSE.txt is kept in this folder.

Review notes. The init and bundle scripts install packages from the npm registry with pnpm, the init script may install pnpm globally, and the bundle script deletes the project `dist` folder and `bundle.html` before rebuilding. No secrets, tokens or personal data were found. The scripts were not executed during installation.
