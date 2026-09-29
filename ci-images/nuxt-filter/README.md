# Nuxt CI tooling

Public tool-only image for Nuxt module checks and Playwright browser tests. It includes Node 24, pnpm 11.24, PostgreSQL 18, ICU and Playwright 1.63's Chromium. It contains no application source or secrets.

The publish workflow runs when the Dockerfile changes on `main`, or manually. Consumers pin its immutable GHCR digest. To update tools, edit the Dockerfile, publish, run the consumer's clean local check twice against the new digest, then update its CI image reference.
