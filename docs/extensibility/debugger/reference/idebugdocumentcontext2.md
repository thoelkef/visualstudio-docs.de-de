---
title: "IDebugDocumentContext2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentContext2"
helpviewer_keywords: 
  - "IDebugDocumentContext2"
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocumentContext2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt eine Position in einer Quelldatei Dokument dar.  
  
## Syntax  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 Das Debugmodul \(DE\) implementiert diese Schnittstelle als Teil ihrer Unterstützung für das Debuggen von Quellcode Ebenen.  Zusätzlich zu einer Position im Quellcode in dieser Schnittstelle stellt Methoden zum Vergleichen von Kontexten sowie zum Navigieren durch ein Quellcode Dokument.  
  
## Hinweise für Aufrufer  
 Methoden in mehreren Schnittstellen, i. d. R. die [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)\-Schnittstellen, geben diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugDocumentContext2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ruft das Dokument ab, das den Dokumentenkontext enthält.|  
|[GetName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ruft den anzeigbaren Namen des Dokuments ab, das den Dokumentenkontext enthält.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Ruft eine Liste aller Code kontexte ab, die diesem Dokumentenkontext zugeordnet sind.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ruft die Sprache ab, die diesem Dokumentenkontext zugeordnet ist.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft die Datei ab kontexts Bereich für dieses Dokument.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ruft den Datei quellbereich dieses Dokument kontexts ab.|  
|[Vergleichen](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Vergleicht den Dokumentenkontext kontexten Dokumente in ein angegebenes Array.|  
|[Suchen](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Verschiebt den Dokumentenkontext durch eine angegebene Anzahl von Anweisungen oder Zeilen.|  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)