---
title: "IDebugDocumentPosition2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentPosition2"
helpviewer_keywords: 
  - "IDebugDocumentPosition2-Schnittstelle"
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# IDebugDocumentPosition2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine abstrakte Position in einer Quelldatei dar.  
  
## Syntax  
  
```  
IDebugDocumentPosition2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Visual Studio normalerweise implementiert diese Schnittstelle.  Ein Modul \(Debug\) DE würde auch diese Schnittstelle implementieren, wenn es über einen eigenen Quellcode angegeben werden muss \(beispielsweise, wenn die DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstelle implementiert\).  
  
## Hinweise für Aufrufer  
 Diese Schnittstelle wird als Argument an [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)übergeben.  Sie wird auch als Teil einer [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union angegeben \(speziell eine [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur\), die wiederum Bestandteil der [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) Struktur ist, die verwendet wird, wenn mithilfe eines ausstehenden Haltepunkt erstellt.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugDocumentPosition2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ruft den Dateinamen der Quelldatei ab, die diesen Dokumenten Zeilenposition enthält.|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ruft das enthaltende Dokument ab.|  
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bestimmt, ob diese bestimmten Position im Dokument enthalten ist.|  
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ruft den Bereich für diese Position des Dokuments ab.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)