FROM onnxmlirczar/onnx-mlir-dev
WORKDIR /workdir
ENV HOME=/workdir

# 1) Install packages.
ENV PATH=$PATH:/workdir/bin
RUN apt-get update
RUN apt-get install -y python-numpy
RUN apt-get install -y python3-pip
RUN python -m pip install --upgrade pip
RUN apt-get install -y gdb
RUN apt-get install -y lldb
RUN apt-get install -y emacs
RUN apt-get install -y vim
# 2) Instal optional packages, uncomment/add as you see fit.
# RUN apt-get install -y valgrind
# RUN apt-get install -y libeigen3-dev
# RUN apt-get install -y clang-format
# RUN python -m pip install wheel
# RUN python -m pip install numpy
# RUN python -m pip install torch==1.6.0+cpu torchvision==0.7.0+cpu -f https://download.pytorch.org/whl/torch_stable.html
# RUN git clone https://github.com/onnx/tutorials.git
# Install clang-12.
# RUN apt-get install -y lsb-release wget software-properties-common
# RUN bash -c "$(wget -O - https://apt.llvm.org/llvm.sh)"

# 3) When using vscode, copy your .vscode in the Dockerfile dir and
#    uncomment the two lines below.
# WORKDIR /workdir/.vscode
# ADD .vscode /workdir/.vscode

# 4) When using a personal workspace folder, set your workspace sub-directory
#    in the Dockerfile dir and uncomment the two lines below.
# WORKDIR /workdir/workspace
# ADD workspace /workdir/workspace

# 5) Fix git by reattaching head and making git see other branches than master.
WORKDIR /workdir/onnx-mlir
RUN git checkout master
RUN git fetch --unshallow

# 6) Set the PATH environment vars for make/debug mode. Replace Debug
#    with Release in the PATH below when using Release mode.
WORKDIR /workdir
ENV MLIR_DIR=/workdir/llvm-project/build/lib/cmake/mlir
ENV NPROC=4
ENV PATH=$PATH:/workdir/onnx-mlir/build/Debug/bin/:/workdir/onnx-mlir/build/Debug/lib:/workdir/llvm-project/build/bin
