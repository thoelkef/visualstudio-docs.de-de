---
title: IDebugFunctionObject2::CreateObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugFunctionObject2::CreateObject
- CreateObject
ms.assetid: 148de615-941e-4b64-ab11-75b692aae465
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 6de1a30a032919a90fbb3d760837d5eeca00feaf
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728479"
---
# <a name="idebugfunctionobject2createobject"></a>IDebugFunctionObject2::CreateObject
Erstellt ein Objekt, das einen Konstruktor mit angegebenen Auswertungsflageinstellungen und einem Timeoutwert verwendet.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateObject (
   IDebugFunctionObject* pConstructor,
   DWORD                 dwArgs,
   IDebugObject*         pArgs[],
   DWORD                 dwEvalFlags,
   DWORD                 dwTimeout,
   IDebugObject**        ppObject
);
```

```csharp
int CreateObject (
   IDebugFunctionObject pConstructor,
   uint                 dwArgs,
   IDebugObject[]       pArgs,
   uint                 dwEvalFlags,
   uint                 dwTimeout,
   out IDebugObject**   ppObject
);
```

## <a name="parameters"></a>Parameter
`pConstructor`\
[in] Ein [IDebugFunctionObject-Objekt,](../../../extensibility/debugger/reference/idebugfunctionobject.md) das den Konstruktor des zu erstellenden Objekts darstellt.

`dwArgs`\
[in] Die Anzahl der `pArg` Parameter im Array. Stellt die Anzahl der Parameter dar, die an den Konstruktor übergeben werden.

`pArgs`\
[in] Ein Array von [IDebugObject-Objekten,](../../../extensibility/debugger/reference/idebugobject.md) das die an den Konstruktor übergebenen Parameter darstellt.

`dwEvalFlags`\
[in] Eine Kombination von Flags aus der EVALFLAGS-Enumeration, die angeben, wie die Auswertung ausgeführt werden soll. [EVALFLAGS](../../../extensibility/debugger/reference/evalflags.md)

`dwTimeout`\
[in] Maximale Wartezeit in Millisekunden, bevor von dieser Methode zurückgegeben wird. Verwenden Sie **INFINITE,** um auf unbestimmte Zeit zu warten.

`ppObject`\
[out] Gibt ein **IDebugObject** zurück, das das neu erstellte Objekt darstellt.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie diese Methode auf, um ein Objekt zu erstellen, das eine Instanz einer Klasse darstellt, oder einen anderen komplexen Typ, der einen Konstruktor, d. h. einen Parameter, erfordert.

## <a name="see-also"></a>Weitere Informationen
- [IDebugFunctionObject2](../../../extensibility/debugger/reference/idebugfunctionobject2.md)
