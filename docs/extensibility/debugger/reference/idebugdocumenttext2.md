---
title: "IDebugDocumentText2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocumentText2"
helpviewer_keywords: 
  - "IDebugDocumentText2-Schnittstelle"
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugDocumentText2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Textdokument dar.  
  
## Syntax  
  
```  
IDebugDocumentText2 : IDebugDocument2  
```  
  
## Hinweise für Implementierer  
 Ein Modul \(Debug\) DE implementiert diese Schnittstelle, wenn der Quellcode, den sie enthalten muss, ist in der Form von Text.  Da dies der gängigste Fall sein, wenn die DE [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)\-Schnittstelle implementiert, sollte sie die `IDebugDocumentText2` auch Schnittstelle implementieren.  
  
## Hinweise für Aufrufer  
 Verwenden Sie die `QueryInterface`\-Methode, um diese Schnittstelle aus einer `IDebugDocument2`\-Schnittstelle zu erhalten.  
  
## Methoden in die Vtable\-Reihenfolge  
 Zusätzlich zu den Methoden der `IDebugDocument2`\-Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Ruft die Größe des Texts an dieser Position im Dokument ab.|  
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Ruft den Text der angegebenen Position im Dokument ab.|  
  
## Hinweise  
 Ein Objekt, das diese Schnittstelle implementiert, muss die <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer>\-Schnittstelle implementieren, die auch <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> stellt die Schnittstelle für ein [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)\-Objekt.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)   
 [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)