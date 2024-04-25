RUSTC := rustc --edition=2021

libanalyze_ffi.so: analyze.rs
	$(RUSTC) --crate-name=analyze_ffi $^ --crate-type=cdylib -o $@
