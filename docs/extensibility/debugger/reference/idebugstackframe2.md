---
title: IDebugStackFrame2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugStackFrame2
helpviewer_keywords:
- IDebugStackFrame2 interface
ms.assetid: bd212a6a-dcc6-4756-a77a-e8dfda38b104
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 37acb9f2984c36130de494108ef4b76a59cc74e7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80719513"
---
# <a name="idebugstackframe2"></a>IDebugStackFrame2
Diese Schnittstelle stellt einen einzelnen Stapelrahmen in einer Aufrufliste in einem bestimmten Thread dar.

## <a name="syntax"></a>Syntax

```
IDebugStackFrame2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Das Debugmodul (DE) implementiert diese Schnittstelle, um einen Stapelrahmen darzustellen.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EnumFrameInfo](../../../extensibility/debugger/reference/idebugthread2-enumframeinfo.md) auf, um eine [IEnumDebugFrameInfo2-Schnittstelle](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md) abzurufen. Rufen Sie [Next](../../../extensibility/debugger/reference/ienumdebugframeinfo2-next.md) auf, um `IDebugStackFrame2` eine [FRAMEINFO-Struktur](../../../extensibility/debugger/reference/frameinfo.md) abzurufen, die die Schnittstelle enthält.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugStackFrame2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetCodeContext](../../../extensibility/debugger/reference/idebugstackframe2-getcodecontext.md)|Ruft den Codekontext für diesen Stapelrahmen ab.|
|[GetDocumentContext](../../../extensibility/debugger/reference/idebugstackframe2-getdocumentcontext.md)|Ruft den Dokumentkontext für diesen Stapelrahmen ab.|
|[GetName](../../../extensibility/debugger/reference/idebugstackframe2-getname.md)|Ruft den Namen des Stapelrahmens ab.|
|[GetInfo](../../../extensibility/debugger/reference/idebugstackframe2-getinfo.md)|Ruft eine Beschreibung des Stapelrahmens ab.|
|[GetPhysicalStackRange](../../../extensibility/debugger/reference/idebugstackframe2-getphysicalstackrange.md)|Ruft eine maschinenabhängige Darstellung des Bereichs physischer Adressen ab, die einem Stapelrahmen zugeordnet sind.|
|[GetExpressionContext](../../../extensibility/debugger/reference/idebugstackframe2-getexpressioncontext.md)|Ruft einen Evaluierungskontext für die Ausdruckauswertung im aktuellen Kontext eines Stapelrahmens und Threads ab.|
|[GetLanguageInfo](../../../extensibility/debugger/reference/idebugstackframe2-getlanguageinfo.md)|Ruft die Sprache ab, die einem Stapelrahmen zugeordnet ist.|
|[GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md)|Ruft eine Beschreibung der Eigenschaften ab, die einem Stapelrahmen zugeordnet sind.|
|[EnumProperties](../../../extensibility/debugger/reference/idebugstackframe2-enumproperties.md)|Erstellt einen Enumerator für Stapelrahmeneigenschaften.|
|[GetThread](../../../extensibility/debugger/reference/idebugstackframe2-getthread.md)|Ruft den Thread ab, der einem Stapelrahmen zugeordnet ist.|

## <a name="remarks"></a>Bemerkungen
 Diese Schnittstelle wird nur abgerufen, wenn das zu debuggende Programm an einem Haltepunkt angehalten wurde (entweder durch einen vom Benutzer festgelegten Haltepunkt oder durch eine Ausnahme). Über diese Schnittstelle kann ein Ausdruckskontext zum Auswerten von Ausdrücken abgerufen werden, eine Liste von Registern kann zurückgegeben oder die Aufrufliste abgerufen und untersucht werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
