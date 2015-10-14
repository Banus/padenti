###############################################################################
# Padenti Library
#
# Copyright (C) 2015  Daniele Pianu <daniele.pianu@ieiit.cnr.it>
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>
###############################################################################

set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -fopenmp -march=native")

include_directories(
	${OpenCV_INCLUDE_DIR}
	${Boost_INCLUDE_DIRS}
	${OpenCL_INCLUDE_DIRS}
    ${PROJECT_SOURCE_DIR}/src
    ${PROJECT_SOURCE_DIR}/src/3rd_party
    ${PROJECT_BINARY_DIR}/kernels
)

set(TEST_LIBRARIES ${OpenCV_LIBS} ${Boost_RANDOM_LIBRARY} ${Boost_SYSTEM_LIBRARY} 
	${Boost_FILESYSTEM_LIBRARY} ${Boost_CHRONO_LIBRARY} ${Boost_LOG_LIBRARY} ${OpenCL_LIBRARIES} pthread)


#add_executable(test_training_set test_training_set.cpp)
#target_link_libraries(test_training_set ${OpenCV_LIBS} ${Boost_RANDOM_LIBRARY} ${Boost_SYSTEM_LIBRARY} ${Boost_FILESYSTEM_LIBRARY})

add_executable(test_tree_trainer test_tree_trainer.cpp)
target_link_libraries(test_tree_trainer ${TEST_LIBRARIES})

add_executable(test_classifier test_classifier.cpp)
target_link_libraries(test_classifier ${TEST_LIBRARIES})

install(TARGETS test_tree_trainer test_classifier DESTINATION share/padenti/test)
install(FILES ${PROJECT_SOURCE_DIR}/test/feature.cl DESTINATION share/padenti/test)
