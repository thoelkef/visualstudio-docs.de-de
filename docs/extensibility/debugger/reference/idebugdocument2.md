---
title: IDebugDocument2 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 36ac127e6cd6e25fd42c4859e723c883ecaffa82
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31109154"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Diese Schnittstelle stellt ein Quelldokument.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in der Regel implementiert diese Schnittstelle. Ein Debugging-Modul (DE) kann auch diese Schnittstelle implementieren, wenn es den Quellcode angeben muss und die Quelle ist nicht auf dem Datenträger vorhanden.  In solchen Fällen auch die DE implementieren würde [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) und [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) Schnittstellen sowie einige zusätzlichen Methoden für die [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) und [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Schnittstellen.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden für die `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, und `IDebugActivateDocumentEvent2` Schnittstellen zurückgeben, die diese Schnittstelle.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 Die folgende Tabelle zeigt die Methoden der `IDebugDocument2`.  
  
|Methode|Beschreibung|  
|------------|-----------------|  
|[getName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einer der verschiedenen Formen ab.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft die Klassen-ID des Dokuments ab.|  
  
## <a name="remarks"></a>Hinweise  
 Diese Schnittstelle wird implementiert, nur, wenn die DE des Quellcodes bereitstellt. Z. B. während des Debuggens Skript auf einer HTML-Seite DE liefert den Quellcode einfügen, da die Quelle heruntergeladen oder dynamisch generiert wird und als eine Datei nicht vorhanden. Beim Debuggen von herkömmlicher Sprachen, z. B. C++, muss diese Schnittstelle nicht implementiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Siehe auch  
 [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)