---
title: Dokumentkontext | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738923"
---
# <a name="document-context"></a>Dokumentkontext
Beim [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen ein *Dokumentkontext*:

- Stellt eine Position in einer Quelldatei dar. Bei Sprachen, in denen die Quelldatei möglicherweise nicht vorhanden ist, identifiziert ein Dokumentkontext eine Position in einem Dokument, die normalerweise von der Laufzeitumgebung generiert wird. Beispielsweise kann ein Skriptmodul ein Dokument aus skriptgesteuert generieren. Weitere Informationen finden Sie unter [Dokumentposition](../../extensibility/debugger/document-position.md).

- Beschreibt eine Position in einem Quelldokument, die einem Codekontext entspricht. Der Symbolhandler ordnet einen Codekontext dem Dokumentationskontext zu, indem er Informationen verwendet, die von einem Compiler oder Interpreter generiert werden.

- Wird von einer [IDebugDocumentContext2-Schnittstelle](../../extensibility/debugger/reference/idebugdocumentcontext2.md) implementiert.

## <a name="see-also"></a>Weitere Informationen
- [Codekontext](../../extensibility/debugger/code-context.md)
- [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbolanbieter Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
