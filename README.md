Slug cleaner buildpack
======================

This buildpack helps large applications get in under the Heroku size limit. It extends `.slugignore` to allow the `!` prefix and repurposes it to mean "run after the build", preventing files from reaching the final slug. Add it to the end of your buildpacks list so it runs last:

```
$ heroku buildpacks:add https://github.com/stevo550/buildpack-slug-cleaner.git
```

Many apps might like to add this to their `.slugignore` file:

```
# Rails asset pipeline cache won't be touched in production
!tmp/cache
# App images should have been compiled into public/
!app/assets/images
```

The easiest way to investigate slug sizes is to do a `heroku run bash` on the last passing build and `du -hs *` from there. Slug sizes are usually something that increase over time, so you might find something useful even off a successful build.

If you find any good suggestions for other languages and frameworks send in a pull request or issue and I'll add it to the above.