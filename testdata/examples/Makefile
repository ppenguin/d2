D2 ?= $(shell which ../../d2)

ifeq ($(D2),)
  $(error d2 not found! Specify absolute path with D2=/path/to/d2)
endif

SVGS := $(shell $(D2) themes | gawk -F':' '/^-/{ printf "out/themex-%03d.svg ",$$2 }')

.PHONY:
all: $(SVGS)

# D2 as dependency to expire results if recompiled
out/themex-%.svg: themex.d2 $(D2)
	$(info Building $@ from $< ...)
	$(D2) -t $$(( 10#$* )) $< $@
