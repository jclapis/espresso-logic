cmake_minimum_required(VERSION 3.12)
project(espresso VERSION 2.0.0)

# Include all the headers
set(ESPRESSO_HEADERS
	espresso-src/copyright.h
	espresso-src/espresso.h
	espresso-src/main.h
	espresso-src/mincov.h
	espresso-src/mincov_int.h
	espresso-src/port.h
	espresso-src/signature.h
	espresso-src/sparse.h
	espresso-src/sparse_int.h
	espresso-src/strdup.h
	espresso-src/utility.h
)


# Include all the source files
set(ESPRESSO_SOURCE_FILES
        espresso-src/black_white.c
        espresso-src/canonical.c
        espresso-src/cofactor.c
        espresso-src/cols.c
        espresso-src/compl.c
        espresso-src/contain.c
        espresso-src/cpu_time.c
        espresso-src/cubestr.c
        espresso-src/cvrin.c
        espresso-src/cvrm.c
        espresso-src/cvrmisc.c
        espresso-src/cvrout.c
        espresso-src/dominate.c
        espresso-src/equiv.c
        espresso-src/espresso.c
        espresso-src/essen.c
        espresso-src/essentiality.c
        espresso-src/exact.c
        espresso-src/expand.c
        espresso-src/gasp.c
        espresso-src/gimpel.c
        espresso-src/globals.c
        espresso-src/hack.c
        espresso-src/indep.c
        espresso-src/irred.c
        espresso-src/main.c
        espresso-src/map.c
        espresso-src/matrix.c
        espresso-src/mincov.c
        espresso-src/opo.c
        espresso-src/pair.c
        espresso-src/part.c
        espresso-src/primes.c
        espresso-src/prtime.c
        espresso-src/reduce.c
        espresso-src/rows.c
        espresso-src/set.c
        espresso-src/setc.c
        espresso-src/sharp.c
        espresso-src/sigma.c
        espresso-src/signature.c
        espresso-src/signature_exact.c
        espresso-src/sminterf.c
        espresso-src/solution.c
        espresso-src/sparse.c
        espresso-src/strdup.c
        espresso-src/unate.c
        espresso-src/util_signature.c
        espresso-src/verify.c
)


# Set the include directories
include_directories(
	espresso-src
)


# Define the executable
add_executable(espresso ${ESPRESSO_SOURCE_FILES} ${ESPRESSO_HEADERS})


# Add DLL support for Windows
if(MSVC)
	target_compile_definitions(espresso 
		PUBLIC "__STDC__"
		PRIVATE "__STDC__")
	target_link_libraries(espresso ${CMAKE_SOURCE_DIR}/lib/wingetopt.lib)
endif()
