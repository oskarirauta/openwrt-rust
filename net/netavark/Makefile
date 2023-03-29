include $(TOPDIR)/rules.mk

PKG_NAME:=netavark
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/containers/netavark.git
PKG_SOURCE_DATA:=2023-03-20
PKG_SOURCE_VERSION:=c2222792c2c95c508c13e69dac55673da7203027
PKG_MIRROR_HASH:=92242b44cec82768a9a14fb5e9e8a25860346a22789c661ace000f705f76f4bd

PKG_MAINTAINER:=Oskari Rauta <oskari.rauta@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:= \
	rust/host \
	protobuf/host

include ../../lang/rust/rust-package.mk
include $(INCLUDE_DIR)/package.mk

define Package/netavark
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  TITLE:=A container network stack
  URL:=https://github.com/containers/netavark
endef

define Package/netavark/description
  Netavark is a rust based network stack for containers. It is being designed to work with Podman but is also
  applicable for other OCI container management applications.
endef

CARGO_VARS += \
	PROTOC=$(STAGING_DIR_HOSTPKG)/bin/protoc

define Build/Compile
	$(call Build/Compile/Cargo,,)
endef

define Package/netavark/install
	$(INSTALL_DIR) $(1)/usr/lib/podman
	$(INSTALL_BIN) ./files/netavark-wrapper $(1)/usr/lib/podman/netavark
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/netavark $(1)/usr/lib/podman/netavark-bin
endef

$(eval $(call RustBinPackage,netavark))
$(eval $(call BuildPackage,netavark))
