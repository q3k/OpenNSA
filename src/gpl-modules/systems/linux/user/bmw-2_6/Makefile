#
#  Copyright 2017 Broadcom
#  
#  This program is free software; you can redistribute it and/or modify
#  it under the terms of the GNU General Public License, version 2, as
#  published by the Free Software Foundation (the "GPL").
#  
#  This program is distributed in the hope that it will be useful, but
#  WITHOUT ANY WARRANTY; without even the implied warranty of
#  MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
#  General Public License version 2 (GPLv2) for more details.
#  
#  You should have received a copy of the GNU General Public License
#  version 2 (GPLv2) along with this source code.
#
# -*- Makefile -*-
# 
# This software is governed by the Broadcom Switch APIs license.
# This license is set out in https://raw.githubusercontent.com/Broadcom-Network-Switching-Software/OpenNSA/master/Legal/LICENSE file.
# 
# Copyright 2007-2020 Broadcom Inc. All rights reserved.

#
# This make job requires the following environment variables to be set:
#
# SDK                - path to StrataXGS SDK root directory
#
# Optionally the following environment variables can be set to
# override the default build server configuration:
#
# PPC_TOOLS_DIR      - path to build tools (if not in PATH already)
# PPC_CROSS_COMPILE  - cross compile tools prefix
# LINUX_INCLUDE      - path to Linux kernel include directory
#

SDK :=$(shell if [ -n "$$SDK" ] ; then\
	echo $$SDK;\
	else\
	cd $(dir $(lastword $(MAKEFILE_LIST))); while /usr/bin/test ! -e RELEASE ; do \
	dir=`cd ../;pwd`;			\
	if [ "$$dir" = "/" ] ; then		\
	   echo Cannot find SDK in $(lastword $(MAKEFILE_LIST)) 1>&2;		\
	   exit 1;				\
	fi ;					\
	cd $$dir;				\
	done ;					\
	pwd;					\
	fi)

ifeq ($(SDK),)					
$(error Please run this in a tree)		
endif 				

export SDK

override kernel_version=2_6
platform=bmw-$(kernel_version)

# Windriver linux version
#WRS_LINUX_VERSION=1.4
#WRS_LINUX_VERSION=2.0

LINUX_MAKE_USER=1
include ${SDK}/make/Make.linux

