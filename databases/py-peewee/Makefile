# $NetBSD: Makefile,v 1.71 2020/12/23 08:07:59 adam Exp $

DISTNAME=	peewee-3.14.0
PKGNAME=	${PYPKGPREFIX}-${DISTNAME}
CATEGORIES=	databases python
MASTER_SITES=	${MASTER_SITE_PYPI:=p/peewee/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	http://docs.peewee-orm.com/
COMMENT=	Small, expressive ORM for PostgreSQL, MySQL and SQLite
LICENSE=	mit

DEPENDS+=	${PYPKGPREFIX}-cython>=0.22.1:../../devel/py-cython
DEPENDS+=	${PYPKGPREFIX}-sqlite3-[0-9]*:../../databases/py-sqlite3

PYTHON_VERSIONED_DEPENDENCIES=	sphinx:build

MAKE_FLAGS+=	SPHINXBUILD=sphinx-build-${PYVERSSUFFIX}

FILES_SUBST+=	PKGMANDIR=${PKGMANDIR}
MESSAGE_SUBST+=	PYPKGPREFIX=${PYPKGPREFIX}

REPLACE_PYTHON+=	pwiz.py

SUBST_CLASSES+=		lpath
SUBST_STAGE.lpath=	pre-configure
SUBST_FILES.lpath=	setup.py
SUBST_VARS.lpath=	BUILDLINK_PREFIX.sqlite3

INSTALLATION_DIRS+=	${PKGMANDIR}/man1

# Let Cython re-generate these files. Fixes build with Python 3.9.
pre-configure:
	${RM} ${WRKSRC}/playhouse/_sqlite_ext.c ${WRKSRC}/playhouse/_sqlite_udf.c

post-build:
	cd ${WRKSRC}/docs && ${BUILD_MAKE_CMD} man

post-install:
	cd ${DESTDIR}${PREFIX}/bin && ${MV} pwiz.py pwiz-${PYVERSSUFFIX} || ${TRUE}
	${INSTALL_MAN} ${WRKSRC}/docs/_build/man/peewee.1 \
		${DESTDIR}${PREFIX}/${PKGMANDIR}/man1/peewee-${PYVERSSUFFIX}.1

.include "../../databases/sqlite3/buildlink3.mk"
.include "../../lang/python/application.mk"
.include "../../lang/python/egg.mk"
.include "../../lang/python/versioned_dependencies.mk"
.include "../../mk/bsd.pkg.mk"
