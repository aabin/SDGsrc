# $NetBSD: Makefile,v 1.18 2021/01/03 07:40:24 taca Exp $

MODNAME=	apcu
PECL_VERSION=	5.1.19
CATEGORIES+=	sysutils

MAINTAINER=	pkgsrc-users@NetBSD.org
COMMENT=	APCu - APC User Cache
LICENSE=	php

PHP_VERSIONS_INCOMPATIBLE=	56

GNU_CONFIGURE_STRICT=	no # --with-pcre-dir is added for all PHP extensions
CONFIGURE_ARGS+=	--enable-${MODNAME}

PLIST_SUBST+=		PKGBASE=${PKGBASE}

DOCDIR=			${PREFIX}/share/doc/${PKGBASE}

INSTALLATION_DIRS=	${DOCDIR}

post-install:
	${INSTALL_DATA} ${WRKSRC}/INSTALL ${DESTDIR}${DOCDIR}

.include "../../lang/php/ext.mk"
.include "../../mk/bsd.pkg.mk"
