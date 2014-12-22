all: checkEnv clean cublas_serial cublas_batched cublas_streams

.PHONY: checkEnv clean

cublas_serial: cublas_serial.c
	mkdir -p bin
	cc -lcublas cublas_serial.c -o bin/cublas_serial.out
cublas_batched: cublas_batched.c
	mkdir -p bin
	cc -lcublas cublas_batched.c -o bin/cublas_batched.out
cublas_streams: cublas_streams.c
	mkdir -p bin
	cc -lcublas cublas_streams.c -o bin/cublas_streams.out

checkEnv:
ifndef CRAY_CUDATOOLKIT_VERSION
	$(error cudatoolkit module not loaded)
endif
ifndef CRAY_PRGENVGNU
        $(error PrgEnv-gnu environment not loaded)
endif

clean:
	rm -rf bin
	rm -f *.o
	rm -f *.mod
