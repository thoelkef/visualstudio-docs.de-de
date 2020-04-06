---
title: IDebugDocumentText2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2
helpviewer_keywords:
- IDebugDocumentText2 interface
ms.assetid: e85f50a3-211c-4220-a9f4-789950ba2782
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5b5def7f6cc4ac5ced91ca0a273ce750003dca20
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731562"
---
# <a name="idebugdocumenttext2"></a>IDebugDocumentText2
Diese Schnittstelle stellt ein Textdokument dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentText2 : IDebugDocument2
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul (DE) implementiert diese Schnittstelle, wenn der Quellcode, den es bereitstellen muss, in Textform ist. Da dies der typischste Fall ist, sollte eine DE, wenn sie `IDebugDocumentText2` die [IDebugDocument2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocument2.md) implementiert, auch die Schnittstelle implementieren.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Verwenden `QueryInterface` Sie die Methode, `IDebugDocument2` um diese Schnittstelle von einer Schnittstelle zu beziehen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Zusätzlich zu den Methoden `IDebugDocument2` auf der Schnittstelle implementiert diese Schnittstelle die folgenden Methoden:

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugdocumenttext2-getsize.md)|Ruft die Größe des Textes an dieser Position im Dokument ab.|
|[GetText](../../../extensibility/debugger/reference/idebugdocumenttext2-gettext.md)|Ruft den Text von der angegebenen Position im Dokument ab.|

## <a name="remarks"></a>Bemerkungen
 Ein Objekt, das diese Schnittstelle <xref:System.Runtime.InteropServices.ComTypes.IConnectionPointContainer> implementiert, muss <xref:System.Runtime.InteropServices.ComTypes.IConnectionPoint> auch die Schnittstelle implementieren, die die Schnittstelle für ein [IDebugDocumentTextEvents2-Objekt](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) bereitstellt.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)
- [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)
