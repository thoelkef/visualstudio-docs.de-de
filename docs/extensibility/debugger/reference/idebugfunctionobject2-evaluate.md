---
title: IDebugFunctionObject2::Evaluate | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::Evaluate
ms.assetid: bc54c652-904b-4297-a6db-faa329684881
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9cd9aafd9157f6d14bb7d37f4ba0301485a35991
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66200688"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Ruft die Funktion und der resultierende Wert als Objekt zurückgegeben.

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
[in] Ein Array von [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) Objekten, die Eingabeparameter darstellt. Dieser Parameter wurde mithilfe einer der Methoden erstellen in dieser Schnittstelle erstellt.

`dwParams`\
[in] Die Anzahl von Parametern in der `ppParams` Array.

`dwEvalFlags`\
[in] Eine Kombination von Flags aus der [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md) -Enumeration, die angeben, wie die Auswertung ausgeführt werden.

`dwTimeout`\
[in] Gibt die maximale Zeit in Millisekunden, warten Sie vor der Rückgabe dieser Methode an. Verwendung **UNENDLICHE** für Warten ohne Timeout.

`ppResult`\
[out] Gibt eine **IDebugObject** , das den Wert der Funktion als ein Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)