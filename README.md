# heroku-buildpack-symlink-fixer

This buildpack fixes all absolute symlinks to points to `/app` instead of the (temporary) build directory.
It's useful if any build step creates absolute symlinks - otherwise they'd break when run.

Important: This buildpack should only be run as the last buildpack in the pipeline; since it
changes all symlinks to point to `/app`, the links will be broken until the build output is moved
to its correct location. If you use any other buildpack after this one, it's at your own risk.
