---
title: IDebugDocumentPosition2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentPosition2
helpviewer_keywords:
- IDebugDocumentPosition2 interface
ms.assetid: 0e838ced-12bb-4efc-b811-2b7c034b77b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 63742f220d5a776fca180a3f9f7fe9c15e04c66a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731641"
---
# <a name="idebugdocumentposition2"></a>IDebugDocumentPosition2
Diese Schnittstelle stellt eine abstrakte Position in einer Quelldatei dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPosition2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Visual Studio implementiert diese Schnittstelle in der Regel. Ein Debugmodul (DE) würde diese Schnittstelle ebenfalls implementieren, wenn es seinen eigenen Quellcode angeben muss (z. B. wenn die DE die [IDebugDocument2-Schnittstelle](../../../extensibility/debugger/reference/idebugdocument2.md) implementiert).

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Diese Schnittstelle wird als Argument an [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)übergeben. Es wird auch als Teil einer [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) Union (insbesondere einer [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) Struktur) geliefert, die wiederum Teil der [BP_REQUEST_INFO-Struktur](../../../extensibility/debugger/reference/bp-request-info.md) ist, die zum Erstellen eines ausstehenden Haltepunkts verwendet wird.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugDocumentPosition2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetFileName](../../../extensibility/debugger/reference/idebugdocumentposition2-getfilename.md)|Ruft den Dateinamen der Quelldatei ab, die diese Dokumentposition enthält.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-getdocument.md)|Ruft das enthaltende Dokument ab.|
|[IsPositionInDocument](../../../extensibility/debugger/reference/idebugdocumentposition2-ispositionindocument.md)|Bestimmt, ob diese Position im angegebenen Dokument enthalten ist.|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md)|Ruft den Bereich für diese Dokumentposition ab.|

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)
- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)
