---
title: IDebugDisassemblyStream2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 98ba08e4ec32aceaf6c265714848939cc6ad9c66
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732047"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Diese Schnittstelle stellt einen Stream von Anweisungen dar.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um die Demontage des Codes eines Programms zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Ein Aufruf der [GetDisassemblyStream-Methode](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) gibt diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugDisassemblyStream2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[Lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest Anweisungen, die von der aktuellen Position im Demontagestrom aus beginnen.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt den Lesezeiger im Demontagestream um eine bestimmte Anzahl von Anweisungen relativ zu einer angegebenen Position.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt einen Codepositionsbezeichner für einen bestimmten Codekontext zurück.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein Codekontextobjekt zurück, das einem angegebenen Codepositionsbezeichner entspricht.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Codepositionsbezeichner zurück, der den aktuellen Codespeicherort darstellt.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument ab, das diesem Demontagestream zugeordnet ist.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Bereich dieses Demontagestreams ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses Demontagestreams ab.|

## <a name="remarks"></a>Bemerkungen
 Der Demontagestrom kann erstellt werden, um den gesamten Adressraum oder nur eine Funktion oder ein Modul innerhalb des Raums darzustellen. Jede Anweisung wird durch eine [DisassemblyData-Struktur dargestellt,](../../../extensibility/debugger/reference/disassemblydata.md) die durch einen Aufruf der [Read-Methode](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) zurückgegeben wird.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)
