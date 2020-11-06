# The set of ppx rewriters for BAP

Provides a BAP-specific ppx rewriter that includes only the blessed set of rewriters that are needed to build and use bap projects. In the future, we may even add our own more specialized rewriters. This package is used by BAP and by BAP plugins via the `bapbuild` tool.

# Adding a new rewriter

The way how ppx rewriters work, unfortuntely, precludes us from adding a new rewriter to a downstream package, e.g., by adding a new dependency directly to the build configuration of a plugin that needs an extra rewriter. Therefore, if a new rewriter is need it has to go through the blessing process and get included into this package. This might change in the future, if we will switch to the dune build system that has a mechanism to build a preprocessor from the specified set of rewriters during the build (essentially this package). Until this, the pull requests are welcome. Just go to the [src/dune](src/dune) file and add the needed rewriter into the `library` stanza.

# Legacy

This project is a mere copy of the `ppx_jane`/`ppx_base` projects with the set of rewriters amended to our needs. E.g., we exclude the js_style rewriter that is not compatible with the code generated by ocamlfind or piqi. We also excluded some other rewriters that we are not using, to speed up the build process and make our code base more reliable.