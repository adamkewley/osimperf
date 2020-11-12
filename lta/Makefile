# makefile for building each sampled commit
#
# the `all` target will install each `commit-to-do/<commit>` into
# `installs/<commit>`, followed by creating a senteniel completion
# files that help `make` can use to track progress.
#
# The reason it's done this way (with a top-level Makefile and
# senteniel files) is so that the build process can be cancelled +
# resumed (each build takes >15 min, and there's hundreds of them, and
# the sample size may be increased later).

INSTALLS_DONE = $(subst commits-to-do/,installs-done/,$(wildcard commits-to-do/*))

# where the opensim installs go
installs/:
	mkdir -p $@

# build + install an opensim commit, then `touch` the output `done`
# file (a sententiel file that marks the install as "complete")
installs/%/done: | installs/
	./install-commit $(subst /,,$(subst installs/,,$(dir $@)))
	touch $@

# `installs-done` is an additional dir containing a list of completed
# installs. It's mostly here to make it easier to track progress from
# a single dir (rather than globbing `installs/**/done`)
installs-done/:
	mkdir -p $@

installs-done/%: installs/%/done | installs-done/
	touch $@

.PHONY: all
# installs take a *very* long time, and the build process deletes
# intermediate dirs (in `install-commit`), so ensure `make` doesn't
# try to nuke an install ever
.PRECIOUS: installs/%/done

all: $(INSTALLS_DONE)
