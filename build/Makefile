build: \
	build_ocaml_source \
	build_c_wrapper \
	build_exec \
	build_main
	
build_ocaml_source: 
	@ocamlopt -output-obj -o ../_build/hello.o ../src/hello/hello.ml 

build_c_wrapper:
	@ocamlc ../src/wrapper/wrapper.c
	@mv wrapper.o ../_build/

build_exec:
	@cp `ocamlc -where`/libcamlrun.a ../_build/hello.a && chmod +w ../_build/hello.a
	@ar r ../_build/hello.a ../_build/hello.o ../_build/wrapper.o

build_main:
	cc -o ../_build/hello -I `ocamlc -where` ../src/wrapper/main.c ../_build/hello.a -lcurses

success:
	@echo "Ok"