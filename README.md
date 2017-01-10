
Introduction
============

This repository contains osx binaries for the mono lldb repository at:

	https://github.com/vargaz/lldb

Usage
=====

The lldb binary is in Release/lldb.

In addition to normal usage, this version supports debugging of JIT code generated by the mono runtime. Run the runtime using the MONO_LLDB env variable to enable this functionality:

	MONO_LLDB=1 lldb --args <mono executable> --debug <app>

Fuctionality is currently limited to stack traces and file/line numbers. The --debug argument is required to get file/line numbers.

Its also possible to attach to runtime processes started with MONO_LLDB=1.

	MONO_LLDB=1 <mono executable> --debug <app>

In another window do:

	lldb -p `pgrep mono`

Recreating the binaries
=======================

1. Clone the repository above
2. Build it using:

	xcodebuild build -workspace lldb.xcworkspace -scheme lldb-tool -configuration Release

3. Copy the binaries by running

	./create-binaries.sh <lldb source dir>

4. Create a release
