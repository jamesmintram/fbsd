# $FreeBSD$

.include <src.opts.mk>

PROG=	fstyp

SRCS=	fstyp.c

MAN=	fstyp.8

WARNS?=	2

.if ${MK_ICONV} == "yes"
CFLAGS+=	-DWITH_ICONV
.endif

.include <bsd.endian.mk>

.if ${TARGET_ENDIANNESS} == 1234
HAS_TESTS=
SUBDIR.${MK_TESTS}+= tests
.endif


CFLAGS+=-I${SRCTOP}/sys

LIBADD=	fstyp

.if ${MK_ZFS} != "no"
LIBADD+=nvpair zfs
.endif

.include <bsd.prog.mk>
