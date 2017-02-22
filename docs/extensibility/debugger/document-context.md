---
title: "Dokumentenkontext | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Debuggen [Debugging-SDK] Kontexten"
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Dokumentenkontext
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In debuggendem ein  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]**Dokumentenkontext**:  
  
-   Stellt eine Position in einer Quelldatei dar.  Für Sprachen, in denen die Quelldatei möglicherweise nicht vorhanden ist, kennzeichnet ein Dokumentenkontext eine Position in einem Dokument, das in der Regel von der Laufzeitumgebung generiert wird.  Zum Beispiel kann ein generierte Skript aus dem Dokument ein Skriptmodul.  Weitere Informationen finden Sie unter [Dokumenten\-Position](../../extensibility/debugger/document-position.md).  
  
-   Beschreibt eine Position in einem Quelldokument, das einem Code Elementkontext entspricht.  Der Code ordnet einen Ereignishandler Symbol für den Lokalisierungskontext Kontext Dokumentation unter Verwendung der Informationen an, die von einem Compiler oder einem Interpreter generiert werden.  
  
-   Wird von einer [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md)\-Schnittstelle implementiert.  
  
## Siehe auch  
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [Symbol\-Anbieter](../../extensibility/debugger/symbol-provider.md)   
 [Symbol\-Provider\-Schnittstellen](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Debugger\-Kontexte](../../extensibility/debugger/debugger-contexts.md)