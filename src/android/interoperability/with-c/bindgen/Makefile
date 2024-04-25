# Makefile for C interop

RUSTC := rustc --edition=2021

# ANCHOR: print_birthday_card
print_birthday_card: main.rs libbirthday_bindgen.rlib libbirthday.so
	$(RUSTC) main.rs -o $@ \
	--extern birthday_bindgen=./libbirthday_bindgen.rlib \
	-Lnative=. -lbirthday \
	-C link-arg='-Wl,-rpath='"`pwd`"
# ANCHOR_END: print_birthday_card

# ANCHOR: libbirthday
libbirthday.so: libbirthday.c
	$(CC) $^ -shared -o $@
# ANCHOR_END: libbirthday

# ANCHOR: libbirthday_bindgen
libbirthday_bindgen.rlib: birthday_bindgen.rs
	$(RUSTC) --crate-type=rlib birthday_bindgen.rs

birthday_bindgen.rs: libbirthday_wrapper.h
	bindgen -o $@ -- $^
# ANCHOR_END: libbirthday_bindgen

# ANCHOR: libbirthday_bindgen_test
libbirthday_bindgen_test: birthday_bindgen.rs
	$(RUSTC) --test $^ -o $@
# ANCHOR_END: libbirthday_bindgen_test

clean:
	$(RM) print_birthday_card libbirthday_bindgen.rlib birthday_bindgen.rs libbirthday.so libbirthday_bindgen_test

run: print_birthday_card
	./print_birthday_card
