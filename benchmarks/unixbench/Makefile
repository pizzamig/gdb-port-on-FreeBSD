# Created by: se
# $FreeBSD: head/benchmarks/unixbench/Makefile 331446 2013-10-23 23:05:52Z eadler $

PORTNAME=	unixbench
PORTVERSION=	4.1.0
PORTREVISION=	1
CATEGORIES=	benchmarks
MASTER_SITES=	http://www.tux.org/pub/tux/benchmarks/System/unixbench/

MAINTAINER=	luca.pizzamiglio@gmail.com
COMMENT=	BYTE magazine's Public Domain benchmark for UNIX

USES=	tar:tgz
SUB_FILES=	unixbench
MAKE_JOBS_UNSAFE=	yes

post-extract:
	${RM} -f ${WRKSRC}/pgms/select

do-install:
	${INSTALL_SCRIPT} ${WRKDIR}/unixbench ${STAGEDIR}${PREFIX}/bin/
	${MKDIR} ${STAGEDIR}${PREFIX}/lib/unixbench
	for f in Run ; do \
		${INSTALL_SCRIPT} ${WRKSRC}/$${f} ${STAGEDIR}${PREFIX}/lib/unixbench/ ; \
	done
	for f in Makefile README ; do \
		${INSTALL_DATA} ${WRKSRC}/$${f} ${STAGEDIR}${PREFIX}/lib/unixbench/ ; \
	done
	${MKDIR} ${STAGEDIR}${PREFIX}/lib/unixbench/pgms
	for f in ${WRKSRC}/pgms/* ; do \
		case $$f in \
	*.awk|*.sh|*perlbench) \
		${INSTALL_SCRIPT} $${f} ${STAGEDIR}${PREFIX}/lib/unixbench/pgms/ ;; \
	*.logo|*.base) \
		${INSTALL_SCRIPT} $${f} ${STAGEDIR}${PREFIX}/lib/unixbench/pgms/ ;; \
	*.orig|*.rej|*~) \
		;;\
	*) \
		${INSTALL_PROGRAM} $${f} ${STAGEDIR}${PREFIX}/lib/unixbench/pgms/ ;; \
		esac ; \
	done
	-${MKDIR} ${STAGEDIR}${PREFIX}/lib/unixbench/testdir
	for f in ${WRKSRC}/testdir/* ; do \
		${INSTALL_DATA} $${f} ${STAGEDIR}${PREFIX}/lib/unixbench/testdir/ ; \
	done

.include <bsd.port.mk>
