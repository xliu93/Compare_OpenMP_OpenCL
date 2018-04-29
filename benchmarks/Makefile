include common/make.config

RODINIA_BASE_DIR := $(shell pwd)

#CUDA_BIN_DIR := $(RODINIA_BASE_DIR)/bin/linux/cuda
OMP_BIN_DIR := $(RODINIA_BASE_DIR)/bin/linux/omp
OPENCL_BIN_DIR := $(RODINIA_BASE_DIR)/bin/linux/opencl

#CUDA_DIRS := backprop bfs cfd gaussian heartwall hotspot kmeans lavaMD leukocyte lud nn	nw srad streamcluster particlefilter pathfinder mummergpu
OMP_DIRS  := backprop bfs kmeans lud particlefilter pathfinder 
OCL_DIRS  := backprop bfs kmeans lud particlefilter pathfinder

#all: CUDA OMP OPENCL
all: OMP OPENCL

OMP:
	cd openmp/backprop;				make;	cp backprop $(OMP_BIN_DIR)
	cd openmp/bfs; 					make;	cp bfs $(OMP_BIN_DIR)
	cd openmp/kmeans/kmeans_openmp;			make;	cp kmeans $(OMP_BIN_DIR)
	cd openmp/lud; 					make;	cp omp/lud_omp $(OMP_BIN_DIR)
	cd openmp/particlefilter;			make;	cp particle_filter $(OMP_BIN_DIR)
	cd openmp/pathfinder;			make;	cp pathfinder $(OMP_BIN_DIR)

OPENCL:
	cd opencl/backprop;			make;	cp backprop $(OPENCL_BIN_DIR)
	cd opencl/bfs;				make;	cp bfs	    $(OPENCL_BIN_DIR)
	cd opencl/kmeans;			make;	cp kmeans	$(OPENCL_BIN_DIR)
	cd opencl/lud/ocl;			make;	cp lud		$(OPENCL_BIN_DIR)
	cd opencl/pathfinder;			make;	cp pathfinder	$(OPENCL_BIN_DIR)
	cd opencl/particlefilter;		make;	cp OCL_particlefilter_naive OCL_particlefilter_single OCL_particlefilter_double $(OPENCL_BIN_DIR)
	
clean: OMP_clean OCL_clean

OMP_clean:
	cd $(OMP_BIN_DIR); rm -f *
	for dir in $(OMP_DIRS) ; do cd openmp/$$dir ; make clean ; cd ../.. ; done

OCL_clean:
	cd $(OPENCL_BIN_DIR); rm -f *
	for dir in $(OCL_DIRS) ; do cd opencl/$$dir ; make clean ; cd ../.. ; done
