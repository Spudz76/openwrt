#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
include $(TOPDIR)/rules.mk

PKG_NAME:=squashfs4
PKG_CPE_ID:=cpe:/a:phillip_lougher:squashfs
PKG_VERSION:=4.7.4
PKG_RELEASE=2

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/plougher/squashfs-tools
PKG_SOURCE_DATE:=2025-11-10
PKG_SOURCE_VERSION:=53e5a67aac42e0bc9ad4a249156d7d549ce7436c
PKG_MIRROR_HASH:=7ce390d95af4b7b4ce768cec18aeb9ac61b8ca413d0ced2c42a81446d9dd8690

HOST_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/host-build.mk
HOST_BUILD_SUBDIR:=$(HOST_BUILD_DIR)/squashfs-tools
HOST_MAKE_VARS += INSTALL_PREFIX="$(HOST_BUILD_PREFIX)"
HOST_MAKE_FLAGS += -C $(HOST_BUILD_SUBDIR)
HOST_MAKE_FLAGS += XATTR_SUPPORT=1 XATTR_DEFAULT=0
HOST_MAKE_FLAGS += GZIP_SUPPORT=1
HOST_MAKE_FLAGS += LZ4_SUPPORT=1
HOST_MAKE_FLAGS += LZMA_XZ_SUPPORT=1
HOST_MAKE_FLAGS += LZO_SUPPORT=1
HOST_MAKE_FLAGS += XZ_SUPPORT=1 XZ_EXTENDED_OPTIONS=1
HOST_MAKE_FLAGS += ZSTD_SUPPORT=1
HOST_MAKE_FLAGS += COMP_DEFAULT=zstd

define Host/Configure
endef

define Host/Compile
	$(call Host/Compile/Default,mksquashfs)
	$(call Host/Compile/Default,unsquashfs)
endef

define Host/Install
	$(call Host/Compile/Default,install)
endef

define Host/Uninstall
	$(call Host/Compile/Default,uninstall)
	$(call Host/Compile/Default,clean)
endef

define Host/Clean
endef

$(eval $(call HostBuild))
