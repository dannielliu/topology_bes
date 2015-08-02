# Makefile for the ROOT test programs.
# This Makefile shows nicely how to compile and link applications
# using the ROOT libraries on all supported platforms.
#
# Copyright (c) 2000 Rene Brun and Fons Rademakers
#
#usage make test
#
# Author: Fons Rademakers, 29/2/2000

#include $(ROOTSYS)/test/Makefile.arch
#ROOTLIBS += -lRooFit

#CXX           =
ObjSuf        = o
SrcSuf        = cxx
ExeSuf        =
DllSuf        = so
OutPutOpt     = -o # keep whitespace after "-o"

OPT           = -g
OPT2          = -g
LD            = g++
LDFLAGS       = $(OPT2)

ROOTCONFIG   := root-config
ROOTLIBS     := $(shell $(ROOTCONFIG) --libs)
LIBS          = $(ROOTLIBS) $(SYSLIBS)

ROOTCFLAGS   := $(shell $(ROOTCONFIG) --cflags)
CXXFLAGS     += $(ROOTCFLAGS)




#file path
#VPATH = /ihepbatch/bes/dusx/common
#------------------------------------------------------------------------------

TOPOLOGYO     = topology.$(ObjSuf) TopologyCategory.$(ObjSuf)\
		ParticleObject.$(ObjSuf)
TOPOLOGYS     = topology.$(SrcSuf) TopologyCategory.$(SrcSuf)\
		ParticleObject.$(SrcSuf)
TOPOLOGY      = topology$(ExeSuf)


OBJS          = $(TOPOLOGYO) 

PROGRAMS      = $(TOPOLOGY)

#------------------------------------------------------------------------------

.SUFFIXES: .$(SrcSuf) .$(ObjSuf) .$(DllSuf)
.PHONY:    clean

all:            $(PROGRAMS)


$(TOPOLOGY):    $(TOPOLOGYO)
		$(LD) $(LDFLAGS) $^ $(LIBS) $(OutPutOpt)$@
		@echo "$@ done"


clean:
		@rm -f $(OBJS) core *.err *.log mclist.txt topo.root log.txt




.SUFFIXES: .$(SrcSuf)

###

.$(SrcSuf).$(ObjSuf):
	$(CXX) $(CXXFLAGS) -c $<
