# =================================================================================================
#
# Developer    : Babak Poursartip
#                Institute for Computational Engineering and Sciences
#                The University of Texas at Austin, TX, USA
#
# Code         : 2D Shallow Water Equation
#
# Last Update  : 02/13/2018
#
# =================================================================================================

#module load c7 intel/17.0 mpich2/3.1.4 phdf5/1.8.15-patch1
# to run the code: mpiexec -n 4 ./main

#F90=mpif90 -CB
#F90=mpif90
F90=h5pfc
#F90=h5fc
#F90=ifort
#F90=ifort -pg  # profiler
#F90= gfortran  # not working because of ifort module
#F90= gfortran -ffree-line-length-none#F90= gfortran -ffree-line-length-none

#FFLAGS=-O2 -qopenmp -g -debug all -debug-parameters all -traceback -check all -fp-stack-check -check bounds -check stack -gen-interfaces -warn interfaces -ftrapuv -fpe0 -CB
#FFLAGS=-O2 -qopenmp
FFLAGS=-O2


SOURCESF=	Parameters_mod.f90 \
					messages_and_errors_mod.f90 \
					Timer_mod.f90 \
					reading_address_file_mod.f90 \
					reading_address_file_smod.f90 \
					reading_partitioned_model_mod.f90 \
					reading_partitioned_model_smod.f90 \
					Inf_mod.f90 \
					Results_mod.f90 \
					ParaviewOutput_mod.f90 \
					solve_network_mod.f90 \
					Driver_Simulation.f90

OBJSF=$(SOURCESF:%.F90=%.o)

#-I${HDF5_INC} -L${HDF5_LIB}
main:$(OBJSF)
	@echo Linking...
	$(F90) $(FFLAGS) $(OBJSF) -o main -I${MPI_DIR} -I${HDF5_INC}
	@echo Done!

%.o   : %.F90
	@echo Compiling...
	$(F90) $(FFLAGS) -c $<

# clean rule for object files
cln  :
	@echo Clean Object files...
	rm -rf *.o main
	rm -rf *.mod main
	rm -rf *.smod main
	rm -rf fort.* main




