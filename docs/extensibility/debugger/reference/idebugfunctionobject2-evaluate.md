---
title: 'IDebugFunctionObject2:: evaluieren | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d87d7d3531d198a1478b4aaa55b354c3ac101302
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80728449"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Ruft die-Funktion auf und gibt den resultierenden Wert als-Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Evaluate (
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwEvalFlags,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate (
   IDebugObject     ppParams,
   uint             dwParams,
   uint             dwEvalFlags,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
in Ein Array von [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekten, das die Eingabeparameter darstellt. Jeder dieser Parameter wurde mithilfe einer der Create-Methoden in dieser Schnittstelle erstellt.

`dwParams`\
in Die Anzahl der Parameter im `ppParams` Array.

`dwEvalFlags`\
in Eine Kombination von Flags aus der [evalflags](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung durchgeführt werden soll.

`dwTimeout`\
in Gibt die maximale Zeit in Millisekunden an, die gewartet werden soll, bevor diese Methode zurückgegeben wird. Verwenden **Sie unbegrenzt,** um unbegrenzt zu warten.

`ppResult`\
vorgenommen Gibt ein **idebugobject** -Objekt zurück, das den Wert der Funktion als Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
