---
title: IDebugDocument2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 23510910fe18c68107e2c497aac5913da1eae963
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66310228"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Diese Schnittstelle stellt ein Quelldokument.

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] in der Regel implementiert diese Schnittstelle. Eine Debug-Engine (DE) kann auch diese Schnittstelle implementieren, muss er den Quellcode angeben und die Quelle ist nicht auf dem Datenträger vorhanden.  In solchen Fällen auch die DE implementieren würde [idebugdocumentcontext2 angegeben](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) und [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) Schnittstellen sowie einige zusätzlichen Methoden für die [ IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) und [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md) Schnittstellen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Methoden für die `IDebugDocumentContext2`, `IDebugDisassemblyStream2`, `IDebugDocumentPosition2`, und `IDebugActivateDocumentEvent2` Schnittstellen zurückgeben, die diese Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugDocument2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einem von mehreren Formaten.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft die Klassen-ID des Dokuments ab.|

## <a name="remarks"></a>Hinweise
 Diese Schnittstelle wird implementiert, nur, wenn die DE des Quellcodes bereitstellt. Z. B. beim Debuggen von Skripts auf einer HTML-Seite, die DE stellt den Quellcode, da die Quelle heruntergeladen wird, oder dynamisch generiert und als Datei auf einem Datenträger nicht vorhanden. Beim Debuggen von herkömmlichen Sprachen wie C++, muss diese Schnittstelle nicht implementiert werden.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)