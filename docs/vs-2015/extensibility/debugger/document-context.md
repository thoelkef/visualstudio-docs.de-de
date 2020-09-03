---
title: Dokument Kontext | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3034c9ca02fca8e91eb1aa5e4d0eb5a2fe1f773f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200580"
---
# <a name="document-context"></a>Dokumentkontext
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Beim [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Debuggen ein **Dokument Kontext**:  
  
- Stellt eine Position in einer Quelldatei dar. Für Sprachen, in denen die Quelldatei möglicherweise nicht vorhanden ist, identifiziert ein Dokument Kontext eine Position in einem Dokument, das in der Regel von der Laufzeitumgebung generiert wird. Beispielsweise kann eine Skript-Engine ein Dokument aus einem Skript generieren. Weitere Informationen finden Sie unter [Document Position](../../extensibility/debugger/document-position.md).  
  
- Beschreibt eine Position in einem Quelldokument, die einem Code Kontext entspricht. Der Symbol Handler ordnet dem Dokumentations Kontext einen Code Kontext zu, wobei die von einem Compiler oder einem Interpreter generierten Informationen verwendet werden.  
  
- Wird von einer [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) -Schnittstelle implementiert.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Code Kontext](../../extensibility/debugger/code-context.md)   
 [Symbol Anbieter](../../extensibility/debugger/symbol-provider.md)   
 [Symbol Anbieter Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)
