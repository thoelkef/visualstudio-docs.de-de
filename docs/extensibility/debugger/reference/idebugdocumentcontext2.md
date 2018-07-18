---
title: IDebugDocumentContext2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocumentContext2
helpviewer_keywords:
- IDebugDocumentContext2
ms.assetid: 2a446c71-8100-4c09-a1cc-fd446bd74030
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 06ff06086c0f293f70af7d9570cf72df4be85608
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31107694"
---
# <a name="idebugdocumentcontext2"></a>IDebugDocumentContext2
Diese Schnittstelle stellt eine Position in einer Datei Quelldokument dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocumentContext2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 Die Debugging-Modul (DE) implementiert diese Schnittstelle als Teil der Unterstützung für Codedebuggen. Zusätzlich zu einer Position im Quellcode stellt diese Schnittstelle Methoden für den Vergleich von Kontexten, und Navigieren durch Quellcodedokuments bereit.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden, die auf mehreren Schnittstellen, i. d. r. die [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md) und [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md) Schnittstellen, zurückgeben, die diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentContext2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)|Ruft das Dokument, das Dokumentenkontext dieses enthält.|  
|[getName](../../../extensibility/debugger/reference/idebugdocumentcontext2-getname.md)|Ruft den angezeigten Namen des Dokuments, das Dokumentenkontext dieses enthält.|  
|[EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)|Ruft eine Liste aller Code Kontexte, die diesem Dokumentenkontext zugeordnet.|  
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugdocumentcontext2-getlanguageinfo.md)|Ruft die diesem Dokumentenkontext zugeordnete Sprache ab.|  
|[GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)|Ruft die Anweisung dateibereichs dieses Kontexts Dokument ab.|  
|[GetSourceRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getsourcerange.md)|Ruft die Datei Quellbereich dieses Kontexts Dokument ab.|  
|[Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)|Vergleicht dieses Dokumentenkontext in ein angegebenes Array von Kontexten Dokument.|  
|[Seek](../../../extensibility/debugger/reference/idebugdocumentcontext2-seek.md)|Verschiebt den Dokumentenkontext durch eine angegebene Anzahl von Anweisungen oder Zeilen an.|  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcanstopevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)   
 [GetDocumentContext](../../../extensibility/debugger/reference/idebugcodecontext2-getdocumentcontext.md)