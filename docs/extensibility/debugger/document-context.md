---
title: Dokumentieren Sie Kontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f97df9bc3c0a40a44379ba37f1b36d79cffb74e
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31098744"
---
# <a name="document-context"></a>Dokumentenkontext
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debuggen, eine **Dokumentenkontext**:  
  
-   Stellt eine Position in einer Quelldatei dar. Für die Sprachen, in dem die Datei möglicherweise nicht vorhanden, identifiziert ein Dokumentenkontext eine Position in einem Dokument in der Regel von der Umgebung zur Laufzeit generiert. Ein Skriptmodul kann z. B. ein Dokument aus einem Skript generieren. Weitere Informationen finden Sie unter [Dokumentposition](../../extensibility/debugger/document-position.md).  
  
-   Beschreibt eine Position in einem Quelldokument, die in einen Codekontext entspricht. Der Handler Symbol ordnet einen Codekontext Dokumentation Kontext, mithilfe der Informationen, die von einem Compiler oder einem Interpreter generiert.  
  
-   Wird implementiert, indem ein [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) Schnittstelle.  
  
## <a name="see-also"></a>Siehe auch  
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [Symbol-Anbieter](../../extensibility/debugger/symbol-provider.md)   
 [Symbol-Anbieter-Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Debuggerkontexte](../../extensibility/debugger/debugger-contexts.md)