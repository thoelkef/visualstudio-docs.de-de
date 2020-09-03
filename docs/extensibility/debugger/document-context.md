---
title: Dokument Kontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 48fe651e69e5e2c97756788cc30e54454c26e51e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738923"
---
# <a name="document-context"></a>Dokument Kontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein *Dokument Kontext*:

- Stellt eine Position in einer Quelldatei dar. Für Sprachen, in denen die Quelldatei möglicherweise nicht vorhanden ist, identifiziert ein Dokument Kontext eine Position in einem Dokument, das in der Regel von der Laufzeitumgebung generiert wird. Beispielsweise kann eine Skript-Engine ein Dokument aus einem Skript generieren. Weitere Informationen finden Sie unter [Document Position](../../extensibility/debugger/document-position.md).

- Beschreibt eine Position in einem Quelldokument, die einem Code Kontext entspricht. Der Symbol Handler ordnet dem Dokumentations Kontext einen Code Kontext zu, wobei die von einem Compiler oder einem Interpreter generierten Informationen verwendet werden.

- Wird von einer [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle implementiert.

## <a name="see-also"></a>Siehe auch
- [Code Kontext](../../extensibility/debugger/code-context.md)
- [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbol Anbieter Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debugger-Kontexte](../../extensibility/debugger/debugger-contexts.md)
