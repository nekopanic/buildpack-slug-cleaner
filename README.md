Slug cleaner buildpack
======================

This buildpack helps large applications get in under the Heroku size limit. It does a couple of neat things:

1. Re-applies `.slugignore` at the end of the build. Usually `.slugignore` is only at the start of the build, leaving a lot of intermediate build artifacts in the slug.
2. Deduplicates files using the [rdfind tool](https://rdfind.pauldreik.se/) so they are only stored once in the slug. Once unpacked into a running dyno they become separate files automatically.

You can find the output of rdfind in the `.rdfind.txt` file compiled into the slug (`heroku run bash` and `cat rdfind.txt` from there).