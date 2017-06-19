cmake_minimum_required(VERSION 2.8)

if(NOT DEFINED CMAKE_TOOLCHAIN_FILE)
  if(DEFINED ENV{VITASDK})
    set(CMAKE_TOOLCHAIN_FILE "$ENV{VITASDK}/share/vita.toolchain.cmake" CACHE PATH "toolchain file")
  else()
    message(FATAL_ERROR "Please define VITASDK to point to your SDK path!")
  endif()
endif()

project(soloud)

include_directories(include)
add_definitions(-DWITH_VITA -Dusleep=sceKernelDelayThread)

add_library(soloud STATIC
	src/core/soloud_fft_lut.cpp
	src/core/soloud_core_setters.cpp
	src/core/soloud_audiosource.cpp
	src/core/soloud_fader.cpp
	src/core/soloud_core_faderops.cpp
	src/core/soloud.cpp
	src/core/soloud_thread.cpp
	src/core/soloud_file.cpp
	src/core/soloud_core_3d.cpp
	src/core/soloud_core_getters.cpp
	src/core/soloud_bus.cpp
	src/core/soloud_core_voiceops.cpp
	src/core/soloud_core_filterops.cpp
	src/core/soloud_fft.cpp
	src/core/soloud_core_basicops.cpp
	src/core/soloud_core_voicegroup.cpp
	src/core/soloud_filter.cpp
	src/filter/soloud_biquadresonantfilter.cpp
	src/filter/soloud_flangerfilter.cpp
	src/filter/soloud_fftfilter.cpp
	src/filter/soloud_dcremovalfilter.cpp
	src/filter/soloud_lofifilter.cpp
	src/filter/soloud_echofilter.cpp
	src/filter/soloud_bassboostfilter.cpp
	src/audiosource/tedsid/soloud_tedsid.cpp
	src/audiosource/tedsid/ted.cpp
	src/audiosource/tedsid/sid.cpp
	src/audiosource/monotone/soloud_monotone.cpp
	src/audiosource/speech/soloud_speech.cpp
	src/audiosource/speech/resonator.cpp
	src/audiosource/speech/klatt.cpp
	src/audiosource/speech/darray.cpp
	src/audiosource/speech/tts.cpp
	src/audiosource/openmpt/soloud_openmpt.cpp
	src/audiosource/sfxr/soloud_sfxr.cpp
	src/audiosource/vic/soloud_vic.cpp
	src/audiosource/wav/soloud_wav.cpp
	src/c_api/soloud_c.cpp
	src/audiosource/wav/stb_vorbis.c

	src/backend/vita/soloud_vita.cpp
)
