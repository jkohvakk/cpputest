CXX := wcl
CC  := wcl
AR := wlib
LINK := wlink
LOG := ALLTESTS.LOG
NULL :=
S := $(NULL) #
C := ,
V := /

-include ../platforms/Dos/platform.mk
include ../platforms/Dos/sources.mk

CFLAGS := \
  -q -c -os -oc -d0 -w=3 -ml -zm \
  -dCPPUTEST_MEM_LEAK_DETECTION_DISABLED=1 \
  -dCPPUTEST_STD_CPP_LIB_DISABLED=1 \
  -i$(CPPUTEST_HOME)/include \
  -i$(CPPUTEST_HOME)/include/Platforms/dos \
  -i$(WATCOM)/h \
  -i$(WATCOM)/h/nt \

CXXFLAGS := $(CFLAGS) -xds

.PHONY: all clean

all: CPPU1$(EXE) CPPU2$(EXE) CPPUEXT1$(EXE) CPPUEXT2$(EXE) CPPUEXT3$(EXE) \
  CPPUEXT4$(EXE)

%.obj: %.cpp
	$(CXX) $(CXXFLAGS) -fo=$(notdir $@) $(subst /,$V, $<)

%.obj: %.c
	$(CC) $(subst /,$V, $(CFLAGS)) -fo=$(notdir $@) $(subst /,$V, $<)

CPPU1$(EXE): $(CPPU_OBJECTS) $(CPPU1_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

CPPU2$(EXE): $(CPPU_OBJECTS) $(CPPU2_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

CPPUEXT1$(EXE): $(CPPU_OBJECTS) $(CPPUEXT_OBJECTS) $(CPPUEXT1_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

CPPUEXT2$(EXE): $(CPPU_OBJECTS) $(CPPUEXT_OBJECTS) $(CPPUEXT2_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

CPPUEXT3$(EXE): $(CPPU_OBJECTS) $(CPPUEXT_OBJECTS) $(CPPUEXT3_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

CPPUEXT4$(EXE): $(CPPU_OBJECTS) $(CPPUEXT_OBJECTS) $(CPPUEXT4_OBJECTS)
	$(LINK) opt quiet,map,stack=50k sys dos file $(subst $S,$C,$(notdir $?)) name $@

clean:
	rm -rf *.obj *.map *.txt *.LOG *.EXE *.err
