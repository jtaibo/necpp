
set( NECLIB necpp )
set( NECEXEC nec2cpp )

set( LIB_SOURCES 
		AntennaInput.h
#		atlas_check.cpp
		BaseInput.h
		c_evlcom.cpp
		c_evlcom.h
		c_evlcom_tb.cpp
		c_geometry.cpp
		c_geometry.h
		c_geometry_tb.cpp
		c_ggrid.cpp
		c_ggrid.h
		c_plot_card.cpp
		c_plot_card.h
		catch.hpp
		common.h
		CurrentInput.h
		electromag.cpp
		electromag.h
		libNEC.cpp
		libnecpp.h
		math_util.h
		math_util_tb.cpp
		matrix_algebra.cpp
		matrix_algebra.h
		matrix_algebra_tb.cpp
		misc.cpp
		misc.h
		nec_context.cpp
		nec_context.h
		nec_context_tb.cpp
		nec_debug.h
		nec_exception.cpp
		nec_exception.h
		nec_ground.cpp
		nec_ground.h
		nec_output.cpp
		nec_output.h
		nec_radiation_pattern.cpp
		nec_radiation_pattern.h
		nec_results.cpp
		nec_results.h
		nec_structure_currents.cpp
		nec_structure_currents.h
		nec_wire.h
		necDiff.cpp
		net_solve.cpp
		PowerBudget.h
		RadiationInput.h
		safe_array.h
		safe_array_tb.cpp
		typesafe_stdint.h
		XGetopt.cpp
		XGetopt.h
	)
set( EXEC_SOURCES 
		nec2cpp.cpp
		nec2cpp.h
	)

add_library (${NECLIB} ${LIB_SOURCES})

# Make sure the compiler can find include files for our necpp library
# when other libraries or executables link to necpp
target_include_directories (${NECLIB} PUBLIC ${CMAKE_CURRENT_SOURCE_DIR})

add_executable (${NECEXEC} ${EXEC_SOURCES})

# Link the executable to the necpp library. Since the necpp library has
# public include directories we will use those link directories when building
# necpp executable
target_link_libraries (${NECEXEC} LINK_PUBLIC ${NECLIB})
