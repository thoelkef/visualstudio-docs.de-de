---
title: Dokumentieren Sie Position | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fecc50de842f628c54878af5fc91b5aeb3adefa4
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345725"
---
# <a name="document-position"></a>Dokumentposition
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine *dokumentieren Position*:

- Stellt eine Abstraktion einer Position in einer Quelldatei an, wie die IDE bekannt. Für die meisten Sprachen kann heute eine Dokumentposition als eine Position in einer Quelldatei betrachtet werden.

- Beschreibt eine Position in einem Quelldokument einer Debug-Engine.

- Wird implementiert, indem ein [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Codekontext](../../extensibility/debugger/code-context.md)
- [Dokumentkontext](../../extensibility/debugger/document-context.md)
- [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbolanbieterschnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)