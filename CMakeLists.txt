cmake_minimum_required(VERSION 3.5)
project(DALIGNER)

set(CMAKE_BUILD_TYPE Debug)
set(CMAKE_C_STANDARD 11)
#set(CMAKE_C_FLAGS "${CMAKE_C_FLAGS} -O3 -Wall -Wextra -Wno-unused-result -fno-strict-aliasing")

set(THREADS_PREFER_PTHREAD_FLAG ON)
find_package(Threads REQUIRED)

set(FILTER_SOURCE_FILES filter.c filter.h)
set(DB_QV_SOURCE_FILES DB.c DB.h QV.c QV.h)
set(COMMON_SOURCE_FILES align.h ${DB_QV_SOURCE_FILES})

set(DALIGNER_SOURCE_FILES
        daligner.c
        ${FILTER_SOURCE_FILES}
        align.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(daligner ${DALIGNER_SOURCE_FILES})
target_link_libraries(daligner Threads::Threads m)

set(HPC_DALIGNER_SOURCE_FILES
        HPC.daligner.c
        ${DB_QV_SOURCE_FILES}
        )

add_executable(hpc.daligner ${HPC_DALIGNER_SOURCE_FILES})
target_link_libraries(hpc.daligner m)

set(LASORT_SOURCE_FILES
        LAsort.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAsort ${LASORT_SOURCE_FILES})
target_link_libraries(LAsort m)

set(LAMERGE_SOURCE_FILES
        LAmerge.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAmerge ${LAMERGE_SOURCE_FILES})
target_link_libraries(LAmerge m)

set(LASHOW_SOURCE_FILES
        LAshow.c
        align.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAshow ${LASHOW_SOURCE_FILES})
target_link_libraries(LAshow m)

set(LADUMP_SOURCE_FILES
        LAdump.c
        align.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAdump ${LADUMP_SOURCE_FILES})
target_link_libraries(LAdump m)

set(LACAT_SOURCE_FILES
        LAcat.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAcat ${LACAT_SOURCE_FILES})
target_link_libraries(LAcat m)

set(LASPLIT_SOURCE_FILES
        LAsplit.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAsplit ${LASPLIT_SOURCE_FILES})
target_link_libraries(LAsplit m)

set(LACHECK_SOURCE_FILES
        LAcheck.c
        align.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAcheck ${LACHECK_SOURCE_FILES})
target_link_libraries(LAcheck m)

set(LAINDEX_SOURCE_FILES
        LAindex.c
        align.c
        ${COMMON_SOURCE_FILES}
        )

add_executable(LAindex ${LAINDEX_SOURCE_FILES})
target_link_libraries(LAindex m)
