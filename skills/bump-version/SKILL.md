---
name: bump-version
description:  Bump the version number of a project.
---
Bump the version of this project:
- Identify all langauges in use by their package managers.
- Identify the current version.
- Bump it.
<rust>
- If 0.X.0: change to 0.X+1.0 unless the user asks for 1.0 or 0.X.1.
- If X.Y.Z change to X+1.0.0
</rust>
