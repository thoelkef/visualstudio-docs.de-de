---
title: IDebugFunctionObject::Auswerten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugFunctionObject::Evaluate
helpviewer_keywords:
- IDebugFunctionObject::Evaluate method
ms.assetid: 29349ea3-d5c1-4135-aa76-ced073ab9683
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 529a5f67c808efa258bc0cb9899f546dbb90d431
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728509"
---
# <a name="idebugfunctionobjectevaluate"></a>IDebugFunctionObject::Evaluate
Ruft die Funktion auf und gibt den resultierenden Wert als Objekt zurück.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Evaluate( 
   IDebugObject** ppParams,
   DWORD          dwParams,
   DWORD          dwTimeout,
   IDebugObject** ppResult
);
```

```csharp
int Evaluate(
   IDebugObject[]   ppParams,
   IntPtr           dwParams,
   uint             dwTimeout,
   out IDebugObject ppResult
);
```

## <a name="parameters"></a>Parameter
`ppParams`\
[in] Ein Array von [IDebugObject-Objekten,](../../../extensibility/debugger/reference/idebugobject.md) die die Eingabeparameter darstellen. Jeder dieser Parameter wurde mit `Create` einer der Methoden in der [IDebugFunctionObject-Schnittstelle](../../../extensibility/debugger/reference/idebugfunctionobject.md) erstellt.

`dwParams`\
[in] Die Anzahl der `ppParams` Parameter im Array.

`dwTimeout`\
[in] Gibt die maximale Wartezeit in Millisekunden an, bevor von dieser Methode zurückgegeben wird. Verwenden `INFINITE` Sie diese Verwendung, um auf unbestimmte Zeit zu warten.

`ppResult`\
[out] Gibt ein [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) zurück, das den Wert der Funktion als Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode richtet einen Aufruf der Funktion ein, die durch das [IDebugFunctionObject-Objekt](../../../extensibility/debugger/reference/idebugfunctionobject.md) dargestellt wird.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject](../../../extensibility/debugger/reference/idebugfunctionobject.md)
