include $(TOPDIR)/rules.mk

PKG_NAME:=aardvark-dns
PKG_VERSION:=1.6.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/containers/aardvark-dns.git
PKG_SOURCE_DATA:=2023-03-20
PKG_SOURCE_VERSION:=a3ed7d9ab30fcf57cff01c465fb329fa0a77aab1
PKG_MIRROR_HASH:=skip

PKG_MAINTAINER:=Oskari Rauta <oskari.rauta@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=rust/host netavark

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

$(eval $(call BuildPackage,aardvark-dns))
