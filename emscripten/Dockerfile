FROM emscripten/emsdk:2.0.10

ENV OPENCV_VERSION=4.11.0

RUN wget -q https://github.com/opencv/opencv/archive/refs/tags/${OPENCV_VERSION}.tar.gz && \
    tar xf ${OPENCV_VERSION}.tar.gz && \
    mkdir opencv-build && \
    cd opencv-build && \
    emcmake cmake ../opencv-${OPENCV_VERSION} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCMAKE_INSTALL_PREFIX=/opt/opencv \
        -DBUILD_SHARED_LIBS=OFF \
        -DBUILD_LIST=core,imgproc,imgcodecs \
        \
        -DENABLE_PIC=OFF \
        -DCPU_BASELINE= \
        -DCPU_DISPATCH= \
        -DCV_TRACE=OFF \
        \
        -DWITH_PROTOBUF=OFF \
        -DBUILD_PROTOBUF=OFF \
        \
        -DBUILD_JPEG=ON \
        -DWITH_JPEG=ON \
        -DBUILD_PNG=ON \
        -DWITH_PNG=ON \
        -DBUILD_ZLIB=ON \
        \
        -DWITH_ADE=OFF \
        -DWITH_1394=OFF \
        -DWITH_FFMPEG=OFF \
        -DWITH_GSTREAMER=OFF \
        -DWITH_GTK=OFF \
        -DWITH_OPENCL=OFF \
        -DWITH_OPENGL=OFF \
        -DWITH_TBB=OFF \
        -DWITH_IPP=OFF \
        -DWITH_ITT=OFF \
        -DWITH_EIGEN=OFF \
        -DWITH_VTK=OFF \
        \
        -DBUILD_TESTS=OFF \
        -DBUILD_PERF_TESTS=OFF \
        -DBUILD_EXAMPLES=OFF \
        -DBUILD_opencv_apps=OFF \
        -DBUILD_opencv_js=OFF && \
    \
    emmake make -j1 && \
    emmake make install && \
    \
    cd / && \
    rm -rf /opencv-${OPENCV_VERSION} /opencv-build ${OPENCV_VERSION}.tar.gz