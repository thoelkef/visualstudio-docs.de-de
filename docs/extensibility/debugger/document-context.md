---
title: Dokumentieren Sie Kontext | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: b121259f9be23d235386d7156ca8d326c5847f87
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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