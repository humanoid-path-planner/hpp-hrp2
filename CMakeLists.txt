# Copyright (c) 2014, 2020 CNRS
# Author: Florent Lamiraux, Guilhem Saurel
#
# This file is part of hpp-hrp2.
# hpp-hrp2 is free software: you can redistribute it
# and/or modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation, either version
# 3 of the License, or (at your option) any later version.
#
# hpp-hrp2 is distributed in the hope that it will be
# useful, but WITHOUT ANY WARRANTY; without even the implied warranty
# of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Lesser Public License for more details.  You should have
# received a copy of the GNU Lesser General Public License along with
# hpp-hrp2.  If not, see
# <http://www.gnu.org/licenses/>.

CMAKE_MINIMUM_REQUIRED(VERSION 3.1)

SET(PROJECT_NAME hpp-hrp2)
SET(PROJECT_DESCRIPTION "Data specific to hrp2 robot for hpp-corbaserver")

SET(PROJECT_USE_CMAKE_EXPORT TRUE)

INCLUDE(cmake/hpp.cmake)
INCLUDE(cmake/python.cmake)

COMPUTE_PROJECT_ARGS(PROJECT_ARGS LANGUAGES CXX)
PROJECT(${PROJECT_NAME} ${PROJECT_ARGS})

FINDPYTHON()

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/hrp2/robot.py
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/hrp2/__init__.py
  DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/hrp2
  )

INSTALL(FILES
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/manipulation/hrp2/robot.py
  ${PROJECT_SOURCE_DIR}/src/hpp/corbaserver/manipulation/hrp2/__init__.py
  DESTINATION ${PYTHON_SITELIB}/hpp/corbaserver/manipulation/hrp2
  )

ADD_LIBRARY(${PROJECT_NAME} INTERFACE)
INSTALL(TARGETS ${PROJECT_NAME} EXPORT ${TARGETS_EXPORT_NAME} DESTINATION lib)
