#Pocketsphinx cmake file

cmake_minimum_required(VERSION 3.4.1)

set(KALDI_ROOT /home/shmyrev/android/kaldi-android/build/kaldi/kaldi)
set(LIB_ROOT /home/shmyrev/android/kaldi-android/build/kaldi/local)

set(API_SOURCES
src/main/cpp/kaldi_recognizer.cc
src/main/cpp/kaldi_recognizer.h
src/main/cpp/model.cc
src/main/cpp/model.h
)

add_library( kaldi_jni SHARED
             build/generated-src/cpp/kaldi_recognizer_wrap.cc
             ${API_SOURCES}
)

include_directories("src/main/cpp" "build/kaldi/kaldi/src" "build/kaldi/local/include")

target_link_libraries( kaldi_jni
             ${KALDI_ROOT}/src/online2/kaldi-online2.a
             ${KALDI_ROOT}/src/decoder/kaldi-decoder.a
             ${KALDI_ROOT}/src/ivector/kaldi-ivector.a
             ${KALDI_ROOT}/src/gmm/kaldi-gmm.a
             ${KALDI_ROOT}/src/nnet3/kaldi-nnet3.a
             ${KALDI_ROOT}/src/tree/kaldi-tree.a
             ${KALDI_ROOT}/src/feat/kaldi-feat.a
             ${KALDI_ROOT}/src/lat/kaldi-lat.a
             ${KALDI_ROOT}/src/hmm/kaldi-hmm.a
             ${KALDI_ROOT}/src/transform/kaldi-transform.a
             ${KALDI_ROOT}/src/cudamatrix/kaldi-cudamatrix.a
             ${KALDI_ROOT}/src/matrix/kaldi-matrix.a
             ${KALDI_ROOT}/src/fstext/kaldi-fstext.a
             ${KALDI_ROOT}/src/util/kaldi-util.a
             ${KALDI_ROOT}/src/base/kaldi-base.a
             ${LIB_ROOT}/lib/libfst.a
             ${LIB_ROOT}/lib/libopenblas_armv7-r0.3.8.dev.a
             ${LIB_ROOT}/lib/libclapack.a
             ${LIB_ROOT}/lib/liblapack.a
             ${LIB_ROOT}/lib/libblas.a
             ${LIB_ROOT}/lib/libf2c.a
             log
             )
