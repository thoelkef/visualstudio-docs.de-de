---
title: IDebugFunctionObject2::Auswerten | Microsoft Docs
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728449"
---
# <a name="idebugfunctionobject2evaluate"></a>IDebugFunctionObject2::Evaluate
Ruft die Funktion auf und gibt den resultierenden Wert als Objekt zurück.

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
[in] Ein Array von [IDebugObject-Objekten,](../../../extensibility/debugger/reference/idebugobject.md) das die Eingabeparameter darstellt. Jeder dieser Parameter wurde mithilfe einer der Create-Methoden in dieser Schnittstelle erstellt.

`dwParams`\
[in] Die Anzahl der `ppParams` Parameter im Array.

`dwEvalFlags`\
[in] Eine Kombination von Flags aus der EVALFLAGS-Enumeration, die angeben, wie die Auswertung ausgeführt werden soll. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden Sie **INFINITE,** um auf unbestimmte Zeit zu warten.

`ppResult`\
[out] Gibt ein **IDebugObject** zurück, das den Wert der Funktion als Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
