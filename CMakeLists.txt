cmake_minimum_required(VERSION 3.25.0)

project(
  testopenglllvm
  VERSION 1.0
  LANGUAGES CXX C)

set (CMAKE_CXX_STANDARD 17)

add_executable(DspFaust DspFaust.cpp)
  
target_compile_definitions(DspFaust PUBLIC JACK_DRIVER=1)
target_compile_definitions(DspFaust PUBLIC MIDICTRL=1)
target_compile_definitions(DspFaust PUBLIC DYNAMIC_DSP=1)
target_compile_definitions(DspFaust PUBLIC BUILD=1)

# Drivers:
# COREAUDIO_DRIVER 1
# ALSA_DRIVER 1
# JACK_DRIVER 1
# PORTAUDIO_DRIVER 1
# RTAUDIO_DRIVER 1
# DUMMY_DRIVER 1
# MIDICTRL 1
# OSCCTRL 1
# SOUNDFILE 1

target_include_directories(DspFaust BEFORE
  PUBLIC "/tmp/tmp.Q5tWC3rp2J/faust/build/faustpfx/include"
)
# target_link_directories(DspFaust BEFORE
#   PRIVATE ${FaustPrefix}/lib
# )

target_link_libraries(DspFaust PRIVATE
  # ${LibFaust}
  /tmp/tmp.Q5tWC3rp2J/faust/build/faustpfx/lib/libfaustwithllvm.a
  # nfd
  # ${FaustPrefix}/lib/${OSCFaust}
  # OSCFaust
  tinfo
  z
  jack
  SDL2
  zstd
  # sndfile
)

# target_link_libraries(DspFaust PUBLIC
#   DspFaust
#   z
#   zstd
#   tinfo
# )