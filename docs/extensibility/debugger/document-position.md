---
title: Dokumentieren Sie Position | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: b59d739c-7572-427f-a70d-4e5df63d02c1
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2f025ca2d73e98f8191969510f866cb7eb1d0eea
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56695953"
---
# <a name="document-position"></a>Dokumentposition
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine *dokumentieren Position*:

-   Stellt eine Abstraktion einer Position in einer Quelldatei an, wie die IDE bekannt. Für die meisten Sprachen kann heute eine Dokumentposition als eine Position in einer Quelldatei betrachtet werden.

-   Beschreibt eine Position in einem Quelldokument einer Debug-Engine.

-   Wird implementiert, indem ein [IDebugDocumentPosition2](../../extensibility/debugger/reference/idebugdocumentposition2.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Codekontext](../../extensibility/debugger/code-context.md)
- [Dokumentkontext](../../extensibility/debugger/document-context.md)
- [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbolanbieterschnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)