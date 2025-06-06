cmake_minimum_required(VERSION 3.31)
project(Stockfish)

set(CMAKE_CXX_STANDARD 20)

include_directories(src)

add_executable(Stockfish
        src/bitboard.cpp
        src/bitboard.h
        src/main.cpp
        src/memory.cpp
        src/memory.h
        src/misc.cpp
        src/misc.h
        src/movegen.cpp
        src/movegen.h
        src/position.cpp
        src/position.h
        src/types.h)

