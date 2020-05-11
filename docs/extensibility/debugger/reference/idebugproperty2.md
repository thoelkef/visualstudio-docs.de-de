---
title: IDebugProperty2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProperty2
helpviewer_keywords:
- IDebugProperty2 interface
ms.assetid: a7d5c70f-a1a5-4120-9f70-184e01c25bff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4b04abdac135143ccbbd1b8e5632bf85c974f29d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721227"
---
# <a name="idebugproperty2"></a>IDebugProperty2
Diese Schnittstelle stellt eine Stapelrahmeneigenschaft, eine Programmdokumenteigenschaft oder eine andere Eigenschaft dar. Die Eigenschaft ist in der Regel das Ergebnis einer Ausdrucksauswertung.

> [!NOTE]
> Diese Verwendung von "property" sollte nicht mit der Bedeutung einer `IDebugProperty2` Membervariablen einer Klasse verwechselt werden, obwohl eine solche Entität darstellen kann.

## <a name="syntax"></a>Syntax

```
IDebugProperty2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um eine bestimmte Art von Wert darzustellen. Der Wert kann z. B. ein numerischer Wert als Ergebnis einer Ausdrucksauswertung, eines Speicherkontexts, der zum Anzeigen von Arbeitsspeicher verwendet wird, oder einer Liste von Registern und deren Werten sein.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [EvaluateSync](../../../extensibility/debugger/reference/idebugexpression2-evaluatesync.md) oder [EvaluateAsync](../../../extensibility/debugger/reference/idebugexpression2-evaluateasync.md) auf, um diese Schnittstelle zu erhalten, die das Ergebnis einer Auswertung darstellt. `IDebugExpression2::EvaluateAsync`gibt diese Schnittstelle zurück, indem eine [IDebugExpressionEvaluationCompleteEvent2-Schnittstelle](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) an das SDM gesendet wird, das wiederum [GetResult](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2-getresult.md) aufruft, um die Eigenschaft abzurufen.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugpropertycreateevent2-getdebugproperty.md) gibt diese Schnittstelle zurück, um das zugeordnete Skriptdokument bereitzustellen.

- [GetReturnValue](../../../extensibility/debugger/reference/idebugreturnvalueevent2-getreturnvalue.md) gibt diese Schnittstelle zurück, um den Rückgabewert einer Funktion darzustellen.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugprogram2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Programms darzustellen, z. B. einen Namen oder einen Speicherkontext.

- [GetDebugProperty](../../../extensibility/debugger/reference/idebugstackframe2-getdebugproperty.md) gibt diese Schnittstelle zurück, um verschiedene Eigenschaften des Stapelrahmens, z. B. lokale Variablen, darzustellen.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugProperty2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md)|Füllt eine [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) Struktur aus, die eine Eigenschaft beschreibt.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md)|Legt den Wert einer Eigenschaft aus einer Zeichenfolge fest.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugproperty2-setvalueasreference.md)|Legt den Wert der Eigenschaft aus dem Wert eines bestimmten Verweises fest.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)|Zählt die Kinder einer Immobilie auf.|
|[GetParent](../../../extensibility/debugger/reference/idebugproperty2-getparent.md)|Gibt das übergeordnete Element einer Eigenschaft zurück.|
|[GetDerivedMostProperty](../../../extensibility/debugger/reference/idebugproperty2-getderivedmostproperty.md)|Gibt die Eigenschaft zurück, die die am häufigsten abgeleitete Eigenschaft einer Eigenschaft beschreibt.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugproperty2-getmemorybytes.md)|Gibt die Speicherbytes zurück, aus denen der Wert einer Eigenschaft besteht.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugproperty2-getmemorycontext.md)|Gibt den Speicherkontext für einen Eigenschaftswert zurück.|
|[GetSize](../../../extensibility/debugger/reference/idebugproperty2-getsize.md)|Gibt die Größe des Eigenschaftswerts in Bytes zurück.|
|[GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)|Gibt einen Verweis auf den Wert dieser Eigenschaft zurück.|
|[GetExtendedInfo](../../../extensibility/debugger/reference/idebugproperty2-getextendedinfo.md)|Gibt die erweiterten Informationen einer Eigenschaft zurück.|

## <a name="remarks"></a>Bemerkungen
 Eine Eigenschaft, wie `IDebugProperty2` sie durch eine Schnittstelle dargestellt wird, kann als Wert mit einem Namen, einem Typ und einer Adresse betrachtet werden. Allgemeiner ausgedrückt kann `IDebugProperty2` ein alles darstellen, was eine hierarchische Struktur hat, mit Eltern und Untergeordnetenknoten.

 Eine Eigenschaft ist in der Regel vorübergehend und dauert beispielsweise nur so lange wie der aktuelle Stapelrahmen. Andererseits dauert ein Verweis, der durch eine [IDebugReference2-Schnittstelle](../../../extensibility/debugger/reference/idebugreference2.md) dargestellt wird, so lange, wie der Wert im Arbeitsspeicher verbleibt.

 Die IDE kann `IDebugProperty2` die Schnittstelle verwenden, um Benutzern das Durchsuchen und Ändern von Eigenschaften zur Laufzeit zu ermöglicht.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)
- [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)
