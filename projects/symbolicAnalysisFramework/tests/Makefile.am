include $(top_srcdir)/config/Makefile.for.ROSE.includes.and.libs
include $(top_srcdir)/projects/symbolicAnalysisFramework/common.for.dep.libs

# ----------test program -------------------
#SAF_BUILD_ROOT = $(top_builddir)/projects/symbolicAnalysisFramework
noinst_PROGRAMS = factPlacer latticePlacer scalarFWDataflow liveDeadVarAnalysisSelfTest dominatorAnalysisSelfTest divAnalysisSelfTest genInterestingCFG genCFG  #pathSensitive sequenceStructAnalysisSelfTest 

# DQ (9/28/2011): These test have been moved to the tests/nonsmoke/functional/roseTests/programAnalysisTests/generalDataFlowAnalysisTests directory.
# constantPropagationTest taintedFlowAnalysisTest

# runtimeBoundAnalysis.C  scalarFWDataflow_example.C
factPlacer_SOURCES = factPlacer.C
latticePlacer_SOURCES = latticePlacer.C
scalarFWDataflow_SOURCES = scalarFWDataflow.C
liveDeadVarAnalysisSelfTest_SOURCES = liveDeadVarAnalysisSelfTest.C
dominatorAnalysisSelfTest_SOURCES = dominatorAnalysisSelfTest.C
divAnalysisSelfTest_SOURCES = divAnalysisSelfTest.C
#sequenceStructAnalysisSelfTest_SOURCES = sequenceStructAnalysisSelfTest.C
#pathSensitive_SOURCES = pathSensitive.C pathSensitive.h
genInterestingCFG_SOURCES = genInterestingCFG.C
genCFG_SOURCES = genCFG.C

# DQ (9/28/2011): These test have been moved to the tests/nonsmoke/functional/roseTests/programAnalysisTests/generalDataFlowAnalysisTests directory.
#constantPropagationTest_SOURCES = constantPropagationTest.C
#taintedFlowAnalysisTest_SOURCES = taintedFlowAnalysisTest.C

# Liao 10/7/2010
# the order of some la files matter:
# e.g. lattice and analysis.la should be listed first
LDADD = $(LIBS_WITH_RPATH) $(ROSE_LIBS) 
#         $(SAF_BUILD_ROOT)/src/analysis/libSafanalysis.la \
#         $(SAF_BUILD_ROOT)/src/simpleAnalyses/libSafsimpleAnalyses.la \
#         $(SAF_BUILD_ROOT)/src/lattice/libSaflattice.la \
#         $(SAF_BUILD_ROOT)/src/common/libSafcommon.la \
#         $(SAF_BUILD_ROOT)/src/cfgUtils/libSafcfgUtils.la \
#         $(SAF_BUILD_ROOT)/src/variables/libSafvariables.la \
#         $(SAF_BUILD_ROOT)/src/state/libSafstate.la \
#         $(SAF_BUILD_ROOT)/src/rwAccessLabeler/libSafrwAccessLabeler.la \
#         $(SAF_BUILD_ROOT)/src/arrIndexLabeler/libSafarrIndexLabeler.la \
#         $(SAF_BUILD_ROOT)/src/external/libSafexternal.la

genInterestingCFG_LDADD = $(LIBS_WITH_RPATH) $(ROSE_LIBS)
genCFG_LDADD = $(LIBS_WITH_RPATH) $(ROSE_LIBS)

check-local:factPlacer latticePlacer scalarFWDataflow 
#pathSensitive
#	./factPlacer    $(srcdir)/test_examples/factPlacer_example.cpp > factPlacer_out
# This test passes all but make distcheck for gcc 4.1.2	
#	./latticePlacer $(srcdir)/test_examples/latticePlacer_example.c > latticePlacer_out
# scalarFWDataflow_example.c is not compilable , Liao
#	./scalarFWDataflow $(srcdir)/test_examples/scalarFWDataflow_example.c > scalarFWDataflow_out
# assertion failure	
#	./pathSensitive $(srcdir)/test_examples/pathSensitive_example.cpp > pathSensitive_out
	./dominatorAnalysisSelfTest $(srcdir)/test_examples/dominator_example.cpp > dominatorAnalysis_out
	./liveDeadVarAnalysisSelfTest $(srcdir)/test_examples/liveDead_example.cpp > liveDeadAnalysis_out
	./divAnalysisSelfTest $(srcdir)/test_examples/div_example.cpp > divAnalysis_out
#	./sequenceStructAnalysisSelfTest $(srcdir)/test_examples/SendRecvMD.cpp > sequenceStructAnalysis_out

EXTRA_DIST =  test_examples 
clean-local:
	rm -rf *.o rose_*.[cC] *.dot *.out rose_*.cpp *.patch *.loT *_out detail.html summary.html index.html dbg_imgs
