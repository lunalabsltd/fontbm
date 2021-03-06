cmake_minimum_required(VERSION 3.0)
project(fontbm)

if(NOT MSVC)
    set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++11 -Wall -Wextra -pedantic")
endif(NOT MSVC)

set(SOURCES
        src/main.cpp
        src/App.cpp
        src/App.h
        src/FontInfo.cpp
        src/FontInfo.h
        src/ProgramOptions.cpp
        src/ProgramOptions.h
        src/GlyphInfo.h
        src/external/cxxopts.hpp
        src/Config.h
        src/external/json.hpp
        src/HelpException.h
        src/utils/extractFileName.h
        src/utils/splitStrByDelim.h
        src/utils/getNumberLen.h
        src/freeType/FtLibrary.h
        src/freeType/FtFont.h
        src/freeType/FtException.h
        src/freeType/FtInclude.h
        src/freeType/FtLibrary.cpp
        src/external/utf8cpp/utf8.h
        src/external/utf8cpp/utf8/core.h
        src/external/utf8cpp/utf8/unchecked.h
        src/external/utf8cpp/utf8/checked.h
        src/external/tinyxml2/tinyxml2.cpp
        src/external/tinyxml2/tinyxml2.h
        src/external/maxRectsBinPack/MaxRectsBinPack.cpp
        src/external/maxRectsBinPack/MaxRectsBinPack.h
        src/external/maxRectsBinPack/Rect.h
        src/external/lodepng/lodepng.h
        src/external/lodepng/lodepng.cpp
        src/freetype2/ft2build.h
        src/freetype2/freetype.h
        src/freetype2/ftadvanc.h
        src/freetype2/ftbbox.h
        src/freetype2/ftbdf.h
        src/freetype2/ftbitmap.h
        src/freetype2/ftbzip2.h
        src/freetype2/ftcache.h
        src/freetype2/ftchapters.h
        src/freetype2/ftcid.h
        src/freetype2/ftdriver.h
        src/freetype2/fterrdef.h
        src/freetype2/fterrors.h
        src/freetype2/ftfntfmt.h
        src/freetype2/ftgasp.h
        src/freetype2/ftglyph.h
        src/freetype2/ftgxval.h
        src/freetype2/ftgzip.h
        src/freetype2/ftimage.h
        src/freetype2/ftincrem.h
        src/freetype2/ftlcdfil.h
        src/freetype2/ftlist.h
        src/freetype2/ftlzw.h
        src/freetype2/ftmac.h
        src/freetype2/ftmm.h
        src/freetype2/ftmodapi.h
        src/freetype2/ftmoderr.h
        src/freetype2/ftotval.h
        src/freetype2/ftoutln.h
        src/freetype2/ftparams.h
        src/freetype2/ftpfr.h
        src/freetype2/ftrender.h
        src/freetype2/ftsizes.h
        src/freetype2/ftsnames.h
        src/freetype2/ftstroke.h
        src/freetype2/ftsynth.h
        src/freetype2/ftsystem.h
        src/freetype2/fttrigon.h
        src/freetype2/fttypes.h
        src/freetype2/ftwinfnt.h
        src/freetype2/t1tables.h
        src/freetype2/ttnameid.h
        src/freetype2/tttables.h
        src/freetype2/tttags.h
        src/freetype2/ftconfig.h
        src/freetype2/ftheader.h
        src/freetype2/ftmodule.h
        src/freetype2/ftoption.h
        src/freetype2/ftstdlib.h
        )

add_definitions(-DLODEPNG_NO_COMPILE_DECODER)

add_executable(fontbm ${SOURCES})
target_link_libraries(fontbm ${COMMON_LIBRARIES} ${FREETYPE_LIBRARIES} "-L./libs/ -l freetype")

add_executable(unit_tests
        src/external/catch.hpp
        src/catchMain.cpp
        src/ProgramOptions.cpp
        src/utils/getNumberLenTest.cpp
        src/utils/splitStrByDelimTest.cpp
        src/utils/extractFileNameTest.cpp
        src/ProgramOptionsTest.cpp
        )
target_link_libraries(unit_tests ${COMMON_LIBRARIES})
