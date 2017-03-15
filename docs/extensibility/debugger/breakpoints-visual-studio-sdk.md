---
title: "Haltepunkte (Visual Studio-SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Haltepunkte"
ms.assetid: acfcabed-9f2f-436c-ad18-7ca2f45d631b
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Haltepunkte (Visual Studio-SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Es gibt drei Typen von Haltepunkten: ausstehend, gebunden und Fehler.  
  
 **Ein anstehender Haltepunkt:**  
  
-   Ist eine Abstraktion, die alle Informationen enthält, die benötigt werden, um einen Haltepunkt zu einem oder mehreren kontexten Code in einem oder mehreren Programmen zu binden.  Jedes Mal, wenn in einem Programm, das die gedebuggte zu laden, dass das Debugmodul ist, alle ausstehenden Haltepunkte überprüft, um festzustellen, ob diese verbunden werden können.  
  
     Ein anstehender Haltepunkt selbst bindet, aber nie in den Code, sondern gesammelt und gesagt, alle gebundenen Haltepunkte enthalten soll, dass er generiert.  
  
-   Wird von einer [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)\-Schnittstelle dargestellt.  
  
 **Ein gebundener Haltepunkt:**  
  
-   Ist eine Abstraktion eines Haltepunkts, der zugeordnet werden oder Begrenzung auf ein einzelnes Code Elementkontext.  Jeder gebundene Haltepunkt wird als Reaktion auf einen anstehenden Haltepunkt generiert.  Ein anstehender Haltepunkt kann mehr als einen gebundenen Haltepunkt jedoch generieren.  
  
     Wenn Code entladen wird, kann ein gebundener Haltepunkt und verwarf aufgehoben werden soll.  
  
-   Wird von einer [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)\-Schnittstelle dargestellt.  
  
 **Ein Fehlerbreakpoint:**  
  
-   Ist eine Abstraktion zur Beschreibung eines Fehlers bei dem Versuch, einen anstehenden Haltepunkt zu einem Code Elementkontext zu binden.  Ein Fehler breakpoint beschreibt einen Fehler im Speicherort oder dem Haltepunkt Ausdruck selbst.  Weitere Informationen finden Sie unter [Binden von Haltepunkten](../../extensibility/debugger/binding-breakpoints.md).  
  
     Der Haltepunkt Fehler kann entweder ein Fehler oder eine Warnung sein.  
  
-   Wird von einer [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)\-Schnittstelle dargestellt.  
  
## Siehe auch  
 [Programs](../../extensibility/debugger/programs.md)   
 [Debugger\-Konzepte](../../extensibility/debugger/debugger-concepts.md)   
 [Codekontext](../../extensibility/debugger/code-context.md)   
 [IDebugBoundBreakpoint2](../../extensibility/debugger/reference/idebugboundbreakpoint2.md)   
 [IDebugPendingBreakpoint2](../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)   
 [IDebugErrorBreakpoint2](../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)