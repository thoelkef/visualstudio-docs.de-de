---
title: IDebugalias::GetICorDebugValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: fd01785fee7ce65296bac940fb19819415139d53
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736479"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Ruft eine verwaltete Codeschnittstelle ab, die den diesem Alias zugeordneten Wert darstellt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetICorDebugValue(
   IUnknown** ppUnk
);
```

```csharp
int GetICorDebugValue(
   out object ppUnk
);
```

## <a name="parameters"></a>Parameter
`ppUnk`\
[out] `IUnknown` Schnittstelle, die den wert darstellt, der diesem Alias zugeordnet ist. Diese Schnittstelle kann für `ICorDebugValue` die Schnittstelle abgefragt werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode gilt nur für `ICorDebugValue` verwaltete Werte (die summiert sich für .NET Framework und ist im .NET Framework SDK in der Datei cordebug.idl definiert).

## <a name="see-also"></a>Weitere Informationen
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
