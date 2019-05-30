---
title: Dokumentieren Sie Kontext | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d15e53d29adc04a82274ebd456027d15b0e41703
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345712"
---
# <a name="document-context"></a>Dokumentkontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine *Dokumentkontext*:

- Stellt eine Position in einer Quelldatei dar. Für Sprachen, in dem die Quelldatei nicht vorhanden sein kann, gibt ein Dokumentenkontext eine Position in einem Dokument, das von der Runtime-Umgebung in der Regel generiert. Beispielsweise kann eine Skript-Engine ein Dokument vom Skript generieren. Weitere Informationen finden Sie unter [dokumentieren Position](../../extensibility/debugger/document-position.md).

- Beschreibt eine Position in einem Quelldokument, das einen Codekontext entspricht. Der Symbol-Handler einen Codekontext Dokumentation Kontext mithilfe der Informationen, die vom eines Compilers oder Interpreters zugeordnet.

- Wird implementiert, indem ein [idebugdocumentcontext2 angegeben](../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle.

## <a name="see-also"></a>Siehe auch
- [Codekontext](../../extensibility/debugger/code-context.md)
- [Symbolanbieter](../../extensibility/debugger/symbol-provider.md)
- [Symbolanbieterschnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)