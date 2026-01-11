# -------------------------------------------------------------
# 1️⃣  Base image – Ubuntu 22.04
# -------------------------------------------------------------
FROM ubuntu:22.04

ENV DEBIAN_FRONTEND=noninteractive

# -------------------------------------------------------------
# 2️⃣  Install base packages and build tools for embedded development
# -------------------------------------------------------------
RUN apt-get update && \
    # Install essential build tools and libraries for embedded development
    apt-get install -y --no-install-recommends \
        build-essential \
        gcc-arm-none-eabi \
        gdb-arm-none-eabi \
        binutils-arm-none-eabi \
        git \
        vim \
        nano \
        python3 \
        python3-pip \
        make \
        curl \
        wget \
        ca-certificates \
        libusb-1.0-0-dev \
        libudev-dev && \
    # Install additional tools for Betaflight development
    apt-get install -y --no-install-recommends \
        dfu-util \
        openocd \
        clang-format && \
    # Clean up apt cache
    rm -rf /var/lib/apt/lists/*

# -------------------------------------------------------------
# 3️⃣  Install Python packages needed for build scripts
# -------------------------------------------------------------
RUN pip3 install --no-cache-dir \
    pyserial \
    intelhex \
    cryptography

# -------------------------------------------------------------
# 4️⃣  Install OpenCode AI assistant
# -------------------------------------------------------------
RUN curl -fsSL https://opencode.ai/install | bash

# -------------------------------------------------------------
# 5️⃣  Set up environment variables for ARM cross-compilation
# -------------------------------------------------------------
ENV PATH="/usr/lib/gcc/arm-none-eabi/11.2.0/bin:${PATH}"
