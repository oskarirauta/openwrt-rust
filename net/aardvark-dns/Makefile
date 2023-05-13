include $(TOPDIR)/rules.mk

PKG_NAME:=aardvark-dns
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/containers/aardvark-dns.git
PKG_SOURCE_DATE:=2023-05-12
PKG_SOURCE_VERSION:=6e06736707d8a84240858e968a54a083083e3a09
PKG_MIRROR_HASH:=e890b089163480a59bfab8c79b7ec89bf6a4a01760a4d3792f7690bfa712e477

PKG_MAINTAINER:=Oskari Rauta <oskari.rauta@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host

include ../../lang/rust/rust-package.mk
include $(INCLUDE_DIR)/package.mk

define Package/aardvark-dns
  SECTION:=net
  CATEGORY:=Network
  DEPENDS:=$(RUST_ARCH_DEPENDS)
  TITLE:=authoritative dns server for container records
  URL:=https://github.com/containers/aardvark-dns
endef

define Package/aardvark-dns/description
  Aardvark-dns is an authoritative dns server for A/AAAA container records.
  It can forward other requests to configured resolvers.

  It is mostly intended to be used with Netavark which will
  launch it automatically if both are installed.
endef

define Build/Compile
	$(call Build/Compile/Cargo,,)
endef

define Package/aardvark-dns/install
	$(INSTALL_DIR) $(1)/usr/lib/podman
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/aardvark-dns $(1)/usr/lib/podman/
endef

$(eval $(call RustBinPackage,aardvark-dns))
$(eval $(call BuildPackage,aardvark-dns))
