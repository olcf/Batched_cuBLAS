all: checkEnv clean cublas_serial cublas_batched cublas_streams

.PHONY: checkEnv clean

cublas_serial: cublas_serial.f90
	mkdir -p bin
	nvcc -c cublas_fortran.cu
	ftn -lcublas cublas_fortran_iso.f90 cublas_serial.f90 cublas_fortran.o -o bin/cublas_serial.out
cublas_batched: cublas_batched.f90
	mkdir -p bin
	nvcc -c cublas_fortran.cu
	ftn -lcublas cublas_fortran_iso.f90 cublas_batched.f90 cublas_fortran.o -o bin/cublas_batched.out
cublas_streams: cublas_streams.f90
	mkdir -p bin
	nvcc -c cublas_fortran.cu
	ftn -lcublas cublas_fortran_iso.f90 cublas_streams.f90 cublas_fortran.o -o bin/cublas_streams.out

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
