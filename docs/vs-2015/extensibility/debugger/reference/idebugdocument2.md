---
title: IDebugDocument2 | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2cd6afb417de4d8a362916f91593d0d0e67d307c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156499"
---
# <a name="idebugdocument2"></a>IDebugDocument2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Diese Schnittstelle stellt ein Quelldokument dar.  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugDocument2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Hinweise für Implementierer  
 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Implementiert in der Regel diese Schnittstelle. Eine Debug-Engine (de) kann diese Schnittstelle auch implementieren, wenn Sie den Quellcode bereitstellen muss und die Quelle auf dem Datenträger nicht vorhanden ist.  In solchen Fällen würde de de auch [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) -und [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) -Schnittstellen sowie einige zusätzliche Methoden für die [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) -und [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) -Schnittstellen implementieren.  
  
## <a name="notes-for-callers"></a>Hinweise für Aufrufer  
 Methoden in den `IDebugDocumentContext2` `IDebugDisassemblyStream2` `IDebugDocumentPosition2` Schnittstellen,, und `IDebugActivateDocumentEvent2` geben diese Schnittstelle zurück.  
  
## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge  
 In der folgenden Tabelle sind die Methoden von aufgeführt `IDebugDocument2` .  
  
|Methode|BESCHREIBUNG|  
|------------|-----------------|  
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einer von mehreren Formularen ab.|  
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft den Klassen Bezeichner des Dokuments ab.|  
  
## <a name="remarks"></a>Bemerkungen  
 Diese Schnittstelle wird nur implementiert, wenn die de den Quellcode bereitstellt. Wenn Sie z. b. das Skript auf einer HTML-Seite Debuggen, stellt das de den Quellcode bereit, da die Quelle heruntergeladen oder dynamisch generiert wird und nicht als Datenträger Datei vorhanden ist. Beim Debuggen von herkömmlichen Sprachen, wie z. b. C++, muss diese Schnittstelle nicht implementiert werden.  
  
## <a name="requirements"></a>Anforderungen  
 Header: msdbg. h  
  
 Namespace: Microsoft. VisualStudio. Debugger. Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ispositionindocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)   
 [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
