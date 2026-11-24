# TOFIX

Findings from a code scan on 2026-10-04.

## Medium

- `README.md:4` - describes a working randomizer ("randomize lists so that you could train on scales, modes and more"), but the repo contains no code at all - the only content is the placeholder `docs/index.html` ("Hello, Js-randomizer"). The working implementation of this idea is `gcp-randomizer` (Flask app with the modes and free-form list pages); either build the JS version or reword the README to point there.
- `docs/index.html:1` - tracked although the fleet `.gitignore` ignores `/docs/index.html` (line 255; `git ls-files -ci --exclude-standard` lists it). Remove the placeholder page from the index, or if it is real Pages content, move it under a path the shared `.gitignore` does not ignore.
- Repo root - no `rsconstruct.toml` and no `.github/workflows/build.yml`, unlike the rest of the fleet, so nothing lints `README.md` or the html. Add the standard fleet `build.yml`, `.github/actionlint.yaml`, `.github/dependabot.yml`, `.rumdl.toml` and an `rsconstruct.toml` with `[processor.rumdl] src_files = ["README.md"]`.
