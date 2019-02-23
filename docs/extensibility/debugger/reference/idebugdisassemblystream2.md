---
title: IDebugDisassemblyStream2 | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDisassemblyStream2
helpviewer_keywords:
- IDebugDisassemblyStream2 interface
ms.assetid: b03cab0c-3f0b-4cc6-88dc-acb3b48c567a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 352d0c71151a7c99822f5ad9f15250c47541fb19
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705819"
---
# <a name="idebugdisassemblystream2"></a>IDebugDisassemblyStream2
Diese Schnittstelle stellt einen Stream von Anweisungen dar.

## <a name="syntax"></a>Syntax

```
IDebugDisassemblyStream2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Ein Debugmodul implementiert diese Schnittstelle, um die Disassembly des Programms Code zu unterstützen.

## <a name="notes-for-callers"></a>Hinweise für Aufrufer
 Ein Aufruf der [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md) Methodenrückgabe diese Schnittstelle.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt die Methoden der `IDebugDisassemblyStream2`.

|Methode|Beschreibung|
|------------|-----------------|
|[Read](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md)|Liest die Anleitung beginnend mit der aktuellen Position im Stream Disassembly.|
|[Seek](../../../extensibility/debugger/reference/idebugdisassemblystream2-seek.md)|Verschiebt des lesezeigers im Disassemblyfenster Stream einer bestimmten Anzahl von Anweisungen, die relativ zur angegebenen Position.|
|[GetCodeLocationId](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodelocationid.md)|Gibt einen Code-Speicherort-Bezeichner für einen bestimmten Code-Kontext zurück.|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcodecontext.md)|Gibt ein für eine angegebene Standortbezeichner Code Context-Objekt zurück.|
|[GetCurrentLocation](../../../extensibility/debugger/reference/idebugdisassemblystream2-getcurrentlocation.md)|Gibt einen Code geographical Location Identifier, die den aktuellen Speicherort darstellt.|
|[GetDocument](../../../extensibility/debugger/reference/idebugdisassemblystream2-getdocument.md)|Ruft das Quelldokument, dem dieser Stream Disassembly zugeordnet ist.|
|[GetScope](../../../extensibility/debugger/reference/idebugdisassemblystream2-getscope.md)|Ruft den Bereich dieses Disassembly-Streams ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugdisassemblystream2-getsize.md)|Ruft die Größe dieses Streams Disassembly.|

## <a name="remarks"></a>Hinweise
 Im gesamten Adressraum oder nur eine Funktion oder dieses Moduls innerhalb des Bereichs darstellt, kann der Disassembly-Stream erstellt werden. Jede Anweisung wird dargestellt, indem eine [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) durch einen Aufruf zurückgegebene Struktur der [lesen](../../../extensibility/debugger/reference/idebugdisassemblystream2-read.md) Methode.

## <a name="requirements"></a>Anforderungen
 Header: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [GetDisassemblyStream](../../../extensibility/debugger/reference/idebugprogram2-getdisassemblystream.md)
- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)