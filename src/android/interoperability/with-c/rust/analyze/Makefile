LIBANALYZE_DIR := ../libanalyze

analyze: main.c $(LIBANALYZE_DIR)/analyze.h $(LIBANALYZE_DIR)/libanalyze_ffi.so
	$(CXX) main.c -I $(LIBANALYZE_DIR) \
	-L $(LIBANALYZE_DIR) -l analyze_ffi \
	-Wl,-rpath="`realpath ../libanalyze`" -o $@ 
