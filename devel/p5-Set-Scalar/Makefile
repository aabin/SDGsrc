# $NetBSD: Makefile,v 1.32 2020/08/31 18:08:50 wiz Exp $
#

DISTNAME=	Set-Scalar-1.29
PKGNAME=	p5-${DISTNAME}
PKGREVISION=	6
CATEGORIES=	net perl5
MASTER_SITES=	${MASTER_SITE_PERL_CPAN:=Set/}

MAINTAINER=	pkgsrc-users@NetBSD.org
HOMEPAGE=	https://metacpan.org/release/Set-Scalar
COMMENT=	Perl5 module for basic set operations
LICENSE=	${PERL5_LICENSE}

PERL5_PACKLIST=		auto/Set/Scalar/.packlist

.include "../../lang/perl5/module.mk"
.include "../../mk/bsd.pkg.mk"
