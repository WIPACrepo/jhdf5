cmake_minimum_required (VERSION 2.8.6)
PROJECT (HDFJAVA_NCSA_HDF_OBJECT_H5 Java)

SET (CMAKE_VERBOSE_MAKEFILE 1)

INCLUDE_DIRECTORIES (
    ${HDFJAVA_NCSA_HDF_OBJECT_H5_SOURCE_DIR}
    ${HDFJAVA_NCSA_HDF_OBJECT_H5_BINARY_DIR}
)

GET_TARGET_PROPERTY(${HDFJAVA_NCSA_HDF5_LIB_TARGET}_JAR_FILE ${HDFJAVA_NCSA_HDF5_LIB_TARGET} JAR_FILE)
SET (CMAKE_JAVA_INCLUDE_PATH ${CMAKE_JAVA_INCLUDE_PATH} ${${HDFJAVA_NCSA_HDF5_LIB_TARGET}_JAR_FILE} ${${HDFJAVA_NCSA_OBJECT_LIB_TARGET}_JAR_FILE})

SET (HDFJAVA_NCSA_HDF_OBJECT_H5_SRCS
    H5CompoundDS.java
    H5Datatype.java
    H5File.java
    H5Group.java
    H5Link.java
    H5ScalarDS.java
)

INCLUDE_DIRECTORIES (${CMAKE_CURRENT_BINARY_DIR}/CMakeFiles/${HDFJAVA_NCSA_H5_LIB_CORENAME}.dir/ncsa/hdf/object/h5)

ADD_JAR (${HDFJAVA_NCSA_H5_LIB_TARGET} ${HDFJAVA_NCSA_HDF_OBJECT_H5_SRCS})
INSTALL_JAR (${HDFJAVA_NCSA_H5_LIB_TARGET} ${HJAVA_INSTALL_LIB_DIR} libraries)
GET_TARGET_PROPERTY(${HDFJAVA_NCSA_H5_LIB_TARGET}_JAR_FILE ${HDFJAVA_NCSA_H5_LIB_TARGET} JAR_FILE)
SET_GLOBAL_VARIABLE (HDFJAVA_JARS_TO_EXPORT "${HDFJAVA_JARS_TO_EXPORT};${${HDFJAVA_NCSA_H5_LIB_TARGET}_JAR_FILE}")

ADD_DEPENDENCIES (${HDFJAVA_NCSA_H5_LIB_TARGET} ${HDFJAVA_NCSA_OBJECT_LIB_TARGET} ${HDFJAVA_NCSA_HDF5_LIB_TARGET})
