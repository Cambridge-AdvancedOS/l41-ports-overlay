#
# The port is based on devel/anytree from the FreeBSD ports by
# arrowd@FreeBSD.org.
#
PORTNAME=	anytree-l41
DISTVERSION=	2.8.0
CATEGORIES=	devel python
PKGNAMEPREFIX=	${PYTHON_PKGNAMEPREFIX}

USE_GITHUB=	yes
GH_ACCOUNT=	RosieBaish
GH_PROJECT=	anytree
GH_COMMIT=	261a7a4a3a6f74a7197a645b8cc47c905eec3c92

MAINTAINER=	konrad.witaszczyk@cl.cam.ac.uk
COMMENT=	Powerful and Lightweight Python Tree Data Structure
WWW=		https://github.com/c0fec0de/anytree

LICENSE=	APACHE20

TEST_DEPENDS=	${PYTHON_PKGNAMEPREFIX}nose>0:devel/py-nose@${PY_FLAVOR} \
		dot:graphics/graphviz

USES=		python
USE_PYTHON=	autoplist distutils

NO_ARCH=	yes

# test_tree_png runs `dot` and returns "Error: Could not find/open font"
# exclude it for now
do-test:
	@cd ${WRKSRC} && ${PYTHON_CMD} -m pytest -v -rs -o addopts= \
	-k 'not test_tree_png'

.include <bsd.port.mk>
