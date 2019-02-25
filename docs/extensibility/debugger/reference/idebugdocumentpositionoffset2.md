---
title: IDebugDocumentPositionOffset2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugDocumentPositionOffset2 interface
ms.assetid: f1b05db3-50d8-453f-a72f-e68b239236a4
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf713ea542901cbde588600d40f144f0fae843e2
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718845"
---
# <a name="idebugdocumentpositionoffset2"></a>IDebugDocumentPositionOffset2
Stellt eine Position in einer Quelldatei als ein Zeichenoffset dar.

## <a name="syntax"></a>Syntax

```
IDebugDocumentPositionOffset2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Durch die IDE implementiert und von Debug-Engines.

## <a name="methods"></a>Methoden
 Die folgende Tabelle zeigt die Methoden der `IDebugDocumentPositionOffset2`.

|Methode|Beschreibung|
|------------|-----------------|
|[GetRange](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2-getrange.md)|Ruft den Bereich für die aktuelle Dokumentposition ab.|

## <a name="remarks"></a>Hinweise
 Dies gibt die gleiche Informationen wie [GetRange](../../../extensibility/debugger/reference/idebugdocumentposition2-getrange.md) aber in `char` offsets vom Anfang des Dokuments. Dies stellt das Dokument, wie es auf einem Datenträger, d. h. ein eindimensionales Array von Zeichen, anstatt der Zeilen- und Spaltennummer vorhanden wäre, der normalerweise zurückgegeben wird.

## <a name="requirements"></a>Anforderungen
 Header: Msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)