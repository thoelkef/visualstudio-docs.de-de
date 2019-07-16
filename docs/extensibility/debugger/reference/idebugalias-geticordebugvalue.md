---
title: IDebugAlias::GetICorDebugValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::GetICorDebugValue
helpviewer_keywords:
- IDebugAlias::GetICorDebugValue method
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f8ef27f9af5626b716339281c010c62c2515fb8b
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746845"
---
# <a name="idebugaliasgeticordebugvalue"></a>IDebugAlias::GetICorDebugValue
Ruft ab eine verwaltete Codeschnittstelle, die den Wert dieser Alias darstellt.

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
[out] `IUnknown` Schnittstelle, die den Wert dieser Alias darstellt. Diese Schnittstelle abgefragt werden kann, für die `ICorDebugValue` Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Diese Methode gilt nur für verwaltete Werte (die `ICorDebugValue` steht eine Schnittstelle in .NET Framework und ist in .NET Framework SDK in der Datei cordebug.idl definiert).

## <a name="see-also"></a>Siehe auch
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)