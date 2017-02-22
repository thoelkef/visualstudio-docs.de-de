---
title: "IDebugDocument2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugDocument2"
helpviewer_keywords: 
  - "IDebugDocument2-Schnittstelle"
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugDocument2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Quelldokument dar.  
  
## Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] normalerweise implementiert diese Schnittstelle.  Ein Modul \(Debug\) DE Darüber hinaus kann diese Schnittstelle implementieren, wenn es den Quellcode und die Quelle angeben, muss auf dem Datenträger nicht vorhanden.  In solchen Fällen wird auch [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) DE [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) und Schnittstellen sowie einige zusätzliche Methoden für [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) und [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)\-Schnittstellen implementieren.  
  
## Hinweise für Aufrufer  
 Methoden für `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`und `IDebugActivateDocumentEvent2`\-Schnittstellen geben diese Schnittstelle zurück.  
  
## Methoden in die Vtable\-Reihenfolge  
 In der folgenden Tabelle werden die Methoden von `IDebugDocument2`an.  
  
|Methode|Beschreibung|  
|-------------|------------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einem von mehreren Formularen ab.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft die Klassen\-ID des Dokuments ab.|  
  
## Hinweise  
 Diese Schnittstelle wird nur supplies DE wenn der Quellcode implementiert.  Wenn Sie z. B. Skripts auf einer HTML\-Seite debuggen, DE supplies der Quellcode, da die Quelle dynamisch und ist nicht als Datenträgerdatei oder heruntergeladen wird.  Bei der herkömmlichen Sprachen wie C\+\+ Debug, muss diese Schnittstelle nicht implementiert werden.  
  
## Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Siehe auch  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)