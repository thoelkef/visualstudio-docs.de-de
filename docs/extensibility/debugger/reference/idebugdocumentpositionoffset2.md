---
title: IDebugDocumentPositionOffset2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d967ec9cf406f7dae691c3f05eda514e0907c7e3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731601"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Stellt eine Position in einer Quelldatei als Zeichenoffset dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Von der IDE implementiert und von Debug-Engines verbraucht.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt `IDebugDocumentPositionOffset2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Ruft den Bereich für die aktuelle Dokumentposition ab.|

## <a name="remarks"></a>Bemerkungen
 Dadurch werden dieselben Informationen wie `char` [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) zurückgegeben, jedoch in Offsets vom Anfang des Dokuments. Dadurch wird das Dokument so dargestellt, als ob es auf einem Datenträger vorhanden wäre, d. h. ein eindimensionales Array von Zeichen anstelle der Zeilen- und Spalteninformationen, die normalerweise zurückgegeben werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)
