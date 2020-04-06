---
title: IDebugReference2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugReference2
helpviewer_keywords:
- IDebugReference2 interface
ms.assetid: 3cfed312-f532-4bce-84a5-1677c14567d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52f655afd35ed316080a3a85ccfae047aa50d87f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720264"
---
# <a name="idebugreference2"></a>IDebugReference2
Diese Schnittstelle stellt einen Verweis auf eine Stackframe-Eigenschaft oder eine andere Eigenschaft dar.

> [!NOTE]
> `IDebugReference2`ist für die zukünftige Verwendung reserviert, `E_NOTIMPL`und alle seine Methoden sollten zurückgegeben werden.

## <a name="syntax"></a>Syntax

```
IDebugReference2 : IUnknown
```

## <a name="notes-for-implementers"></a>Hinweise für Implementierer
 Die DE implementiert diese Schnittstelle, um einen Verweis auf eine bestimmte Art von Wert darzustellen. Der Wert kann z. B. ein numerischer Wert als Ergebnis einer Ausdrucksauswertung, eines Speicherkontexts, der zum Anzeigen von Arbeitsspeicher verwendet wird, oder einer Liste von Registern und deren Werten sein.

## <a name="notes-for-callers"></a>Hinweise für Anrufer
 Rufen Sie [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md) auf, um diese Schnittstelle abzurufen. [GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md) und [GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md) geben auch diese Schnittstelle zurück.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge
 Die folgende Tabelle zeigt `IDebugReference2`die Methoden von .

|Methode|BESCHREIBUNG|
|------------|-----------------|
|[GetReferenceInfo](../../../extensibility/debugger/reference/idebugreference2-getreferenceinfo.md)|Ruft die [DEBUG_REFERENCE_INFO-Struktur](../../../extensibility/debugger/reference/debug-reference-info.md) ab, die diesen Verweis beschreibt.|
|[SetValueAsString](../../../extensibility/debugger/reference/idebugreference2-setvalueasstring.md)|Legt den Wert dieses Verweises aus einer Zeichenfolge fest.|
|[SetValueAsReference](../../../extensibility/debugger/reference/idebugreference2-setvalueasreference.md)|Legt den Wert dieser Referenz aus einem anderen Verweis fest.|
|[EnumChildren](../../../extensibility/debugger/reference/idebugreference2-enumchildren.md)|Zählt die Kinder dieser Referenz auf.|
|[GetParent](../../../extensibility/debugger/reference/idebugreference2-getparent.md)|Ruft das übergeordnete Element dieses Verweises ab.|
|[GetDerivedMostReference](../../../extensibility/debugger/reference/idebugreference2-getderivedmostreference.md)|Ruft den am häufigsten abgeleiteten Verweis dieses Verweises ab.|
|[GetMemoryBytes](../../../extensibility/debugger/reference/idebugreference2-getmemorybytes.md)|Ruft die Speicherbytes ab, auf die dieser Verweis verweist.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugreference2-getmemorycontext.md)|Ruft einen Speicherkontext für diesen Verweis ab.|
|[GetSize](../../../extensibility/debugger/reference/idebugreference2-getsize.md)|Ruft die Größe dieses Verweises in Bytes ab.|
|[SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)|Legt diesen Referenztyp fest.|
|[Vergleichen](../../../extensibility/debugger/reference/idebugreference2-compare.md)|Vergleicht diesen Verweis mit einem anderen.|

## <a name="remarks"></a>Bemerkungen

> [!NOTE]
> Diese Verwendung von "property" sollte nicht mit der Bedeutung einer `IDebugReference2` Membervariablen einer Klasse verwechselt werden, obwohl eine solche Entität darstellen kann.

- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) stellt eine `IDebugReference2` Eigenschaft dar, während sie einen Verweis auf eine Eigenschaft darstellt, in der Regel einen Verweis auf ein Objekt in dem zu debuggenden Programm.

 Der Hauptunterschied zwischen einer Eigenschaft und einem Verweis besteht darin, dass eine Eigenschaft auf eine benannte Instanz eines Objekts verweist, während ein Verweis auf eine unbenannte Instanz verweist. Eine Eigenschaft kann z. B. auf ein Objekt `"a.b"`im Heap des Programms durch verweisen. Eine andere Eigenschaft kann auf `"c.d"`dasselbe Objekt wie verweisen. Die Art und Weise, `"a.b"` wie `"c.d"` auf diese Eigenschaft verwiesen wird, erfordert dies oder ist im Anwendungsbereich. Ein Verweis auf dasselbe Objekt ist namenlos. Auf das Objekt kann verwiesen werden, solange der Speicher für dieses Objekt gültig ist.

 Eine `IDebugProperty2` Schnittstelle kann als Wert mit einem Namen, einem Typ und einer Adresse betrachtet werden. Ein `IDebugReference2`kann dagegen als Typ und Adresse betrachtet werden.

## <a name="requirements"></a>Requirements (Anforderungen)
 Kopfzeile: msdbg.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Wichtige Schnittstellen](../../../extensibility/debugger/reference/core-interfaces.md)
- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)
- [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)
- [GetReference](../../../extensibility/debugger/reference/idebugproperty2-getreference.md)
