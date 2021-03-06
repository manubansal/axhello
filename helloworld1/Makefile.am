#------------------------
# helloworld1
#------------------------

include $(ATOMIX_ROOT_VAL)/Makefile.am.common

EXTRA_PROGRAMS = app_helloworld1

app_helloworld1_SOURCES = \
   main.c \
   setup.c


#app_helloworld1_CFLAGS=-DENABLE_TIMING
app_helloworld1_CFLAGS=

nodist_app_helloworld1_SOURCES = \
   __fifos__.h \
   __fifos__.c \
   __atoms__.h \
   __atoms__.c \
   __actions__.h \
   __actions__.c \
   __states__.h \
   __states__.c

app_helloworld1_CLEANFILES = \
   __fifos__.h \
   __fifos__.c \
   __atoms__.h \
   __atoms__.c \
   __actions__.h \
   __actions__.c \
   __states__.h \
   __states__.c

EXTRA_DIST = \
   fifos.or \
   atoms.or \
   states.or

app_helloworld1_LDADD = \
   $(ATOMIX_INSTALL_DIR_VAL)/osl/lib.osl.a \
   $(ATOMIX_INSTALL_DIR_VAL)/oros/sfifos/lib/edmadriver/lib.oros.sfifos.edmadriver.a \
   $(ATOMIX_INSTALL_DIR_VAL)/oros/sfifos/lib/ipc/lib.oros.sfifos.ipc.a \
   $(ATOMIX_INSTALL_DIR_VAL)/oros/sfifos/ilib/lib.oros.sfifos.ilib.a \
   $(ATOMIX_INSTALL_DIR_VAL)/oros/sfifos/lib.oros.sfifos.a \
   $(ATOMIX_INSTALL_DIR_VAL)/oros/sysilib/lib.oros.sysilib.a \
   $(ATOMIX_INSTALL_DIR_VAL)/exilib/lib.exilib.a \
   $(ATOMIX_INSTALL_DIR_VAL)/osl/lib.osl.vitdec.a \
   $(ATOMIX_INSTALL_DIR_VAL)/osl/lib.osl.platform.a 
if !DEVICE_IS_6638K2K
   app_helloworld1_LDADD += $(ATOMIX_INSTALL_DIR_VAL)/osl/lib.osl.eth.a 
endif

app_helloworld1_CFLAGS += -I"`_cygpath -m $(top_srcdir)`"
app_helloworld1_CFLAGS += -I.

ILIB_INCLUDE_PATH  =
ILIB_INCLUDE_PATH += -I"`_cygpath -m ${ATOMIX_ROOT}/exilib`"
ILIB_INCLUDE_PATH += -I"`_cygpath -m ${ATOMIX_ROOT}/oros/sfifos/ilib`"
ILIB_INCLUDE_PATH += -I"`_cygpath -m ${ATOMIX_ROOT}/oros/sysilib`"

app_helloworld1_CFLAGS += ${ILIB_INCLUDE_PATH}

app_helloworld1_LDFLAGS=\
  -I"${CSL_ROOT}/ti/csl/lib"  \
  -I"${DSPLIB_ROOT}/packages/ti/dsplib/lib"

if DEVICE_IS_6638K2K
  app_helloworld1_LDFLAGS+=\
  -I"${CSL_ROOT}/ti/drv/qmss/lib/c66" \
  -I"${CSL_ROOT}/ti/drv/cppi/lib/c66" \
  -I"${CSL_ROOT}/ti/drv/pa/lib/c66" \
  -I"${CSL_ROOT}/ti/platform/evmk2h/platform_lib/lib/debug"
else
  app_helloworld1_LDFLAGS+=\
  -I"${CSL_ROOT}/ti/drv/qmss/lib" \
  -I"${CSL_ROOT}/ti/drv/cppi/lib" \
  -I"${CSL_ROOT}/ti/drv/pa/lib" \
  -I"${CSL_ROOT}/ti/platform/evmc6670l/platform_lib/lib/debug"
endif

#overriding rule to avoid regenerating source code when no update occurs to source file
APP_HELLOWORLD1_OUT_GENERATED_FILES = fifos atoms actions states
APP_HELLOWORLD1_OUT_SRCDIR = $(top_srcdir)/helloworld1
APP_HELLOWORLD1_OUT_BLDDIR = .


app_helloworld1$(EXEEXT): $(APP_HELLOWORLD1_OUT_GENERATED_FILES) $(app_helloworld1_OBJECTS) $(app_helloworld1_DEPENDENCIES) $(EXTRA_app_helloworld1_DEPENDENCIES) 
	@rm -f app_helloworld1$(EXEEXT)
	$(app_helloworld1_LINK) $(app_helloworld1_LDFLAGS) $(app_helloworld1_OBJECTS) $(app_helloworld1_LDADD) $(LIBS) $(wildcard __*_j_*.c)


$(APP_HELLOWORLD1_OUT_GENERATED_FILES): %: __%__.c

__%__.c: \
	$(APP_HELLOWORLD1_OUT_SRCDIR)/fifos.or \
	$(APP_HELLOWORLD1_OUT_SRCDIR)/atoms.or \
	$(APP_HELLOWORLD1_OUT_SRCDIR)/states.or \
	$(APP_HELLOWORLD1_OUT_SRCDIR)/debug.or
	_create_afs_i \
		$(APP_HELLOWORLD1_OUT_SRCDIR)/fifos.or \
		$(APP_HELLOWORLD1_OUT_SRCDIR)/atoms.or \
		$(APP_HELLOWORLD1_OUT_SRCDIR)/states.or \
		$(APP_HELLOWORLD1_OUT_BLDDIR)/__fifos__.h \
		$(APP_HELLOWORLD1_OUT_BLDDIR)/__fifos__.c \
		$(APP_HELLOWORLD1_OUT_BLDDIR)/__atoms__.h \
	        $(APP_HELLOWORLD1_OUT_BLDDIR)/__atoms__.c \
	        $(APP_HELLOWORLD1_OUT_BLDDIR)/__actions__.h \
	        $(APP_HELLOWORLD1_OUT_BLDDIR)/__actions__.c \
	        $(APP_HELLOWORLD1_OUT_BLDDIR)/__states__.h \
	        $(APP_HELLOWORLD1_OUT_BLDDIR)/__states__.c \
		$(APP_HELLOWORLD1_OUT_SRCDIR)/code_placement.or \
		$(APP_HELLOWORLD1_OUT_SRCDIR)/debug.or \
		${ATOMIX_ROOT}/memorymaps/$(MEMORYMAP_FILE) \
		$(APP_HELLOWORLD1_OUT_BLDDIR)/__memorymap__.cmd \
		${ILIB_INCLUDE_PATH} ${CFLAGS} ${app_helloworld1_CFLAGS}
	if [[ ! -d ${TRACE_DIR} ]]; then mkdir -p ${TRACE_DIR}; fi



helloworld1: app_helloworld1$(EXEEXT)
#	execute app_helloworld1$(EXEEXT)

.PHONY: helloworld1


dist_doc_DATA = README


###########################################
#common to all binary builds
###########################################
if DEVICE_IS_6638K2K
  LDFLAGS+=--LINKER_FLAGS_FILE "`_cygpath -w \"${ATOMIX_ROOT}/linkerflags_k2k.cmd\"`"
else
  LDFLAGS+=--LINKER_FLAGS_FILE "`_cygpath -w \"${ATOMIX_ROOT}/linkerflags.cmd\"`"
endif
app_helloworld1_LDFLAGS+=\
--LINKER_SCRIPT_FILE "`_cygpath -w \"__memorymap__.cmd\"`"

