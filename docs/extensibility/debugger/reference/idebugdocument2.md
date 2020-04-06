---
title: IDebugDocument2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocument2
helpviewer_keywords:
- IDebugDocument2 interface
ms.assetid: 1bc58426-dbf5-4471-9aad-9d66cd80eef0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4c959c018dd4da0ff088c4fb52c0420de83b4eac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731990"
---
# <a name="idebugdocument2"></a>IDebugDocument2
Diese Schnittstelle stellt ein Quelldokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocument2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]implementiert diese Schnittstelle in der Regel. Ein Debugmodul (DE) kann diese Schnittstelle auch implementieren, wenn es den Quellcode bereitstellen muss und die Quelle nicht auf dem Datenträger vorhanden ist.  In solchen Fällen implementiert die DE auch [IDebugDocumentContext2-](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) und [IDebugActivateDocumentEvent2-Schnittstellen](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) sowie einige zusätzliche Methoden auf den [Schnittstellen IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) und [IDebugDocumentPosition2.](../../../extensibility/debugger/reference/idebugdocumentposition2.md)

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Methoden für `IDebugDocumentContext2` `IDebugDisassemblyStream2`die `IDebugDocumentPosition2`, `IDebugActivateDocumentEvent2` , und Schnittstellen geben diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugDocument2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetName](../../../extensibility/debugger/reference/idebugdocument2-getname.md)|Ruft den Namen des Dokuments in einem von mehreren Formularen ab.|
|[GetDocumentClassID](../../../extensibility/debugger/reference/idebugdocument2-getdocumentclassid.md)|Ruft den Klassenbezeichner des Dokuments ab.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird nur implementiert, wenn die DE den Quellcode bereitstellt. Wenn Sie beispielsweise Skripts auf einer HTML-Seite debuggen, liefert die DE den Quellcode, da die Quelle dynamisch heruntergeladen oder generiert wird und nicht als Datenträgerdatei vorhanden ist. Beim Debuggen traditioneller Sprachen, z. B. C++, muss diese Schnittstelle nicht implementiert werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugactivatedocumentevent2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentcontext2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)
- [GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)
