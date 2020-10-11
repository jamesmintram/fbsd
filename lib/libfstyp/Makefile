# $FreeBSD$

.include <src.opts.mk>

LIB=		fstyp
SHLIB_MAJOR=	0
INCS= 		fstyp.h	
MAN=		
MLINKS=		

CFLAGS+=	-I${.CURDIR}

SRCS= apfs.c cd9660.c exfat.c ext2fs.c fstyp.c hammer.c	\
	hammer2.c hfsplus.c msdosfs.c ntfs.c ufs.c  geli.c

.if ${MK_ZFS} != "no"
SRCS +=	zfs.c
.endif

WARNS?=	2

.if ${MK_ICONV} == "yes"
CFLAGS+=	-DWITH_ICONV
.endif

.if ${MK_ZFS} != "no"
IGNORE_PRAGMA=  YES

CFLAGS+= -DNEED_SOLARIS_BOOLEAN -DHAVE_ZFS
CFLAGS+= -I${SRCTOP}/sys/cddl/compat/opensolaris
CFLAGS+= -I${SRCTOP}/cddl/compat/opensolaris/include
CFLAGS+= -I${SRCTOP}/cddl/compat/opensolaris/lib/libumem
CFLAGS+= -I${SRCTOP}/cddl/contrib/opensolaris/lib/libnvpair
CFLAGS+= -I${SRCTOP}/cddl/contrib/opensolaris/lib/libzpool/common
CFLAGS+= -I${SRCTOP}/sys/cddl/contrib/opensolaris/uts/common/fs/zfs
CFLAGS+= -I${SRCTOP}/sys/cddl/contrib/opensolaris/uts/common
CFLAGS+= -I${SRCTOP}/cddl/contrib/opensolaris/head
.endif

CFLAGS+=-I${SRCTOP}/sys
CFLAGS+= -I${SRCTOP}/sys/lib/libufs/

LIBADD=	geom md ufs 

.include <bsd.lib.mk>
