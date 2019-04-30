---
title: IDebugBinder3::FindAlias | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 58675b5f9e963ec416a2c8586375a94f9c06ae69
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62877522"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Diese Methode sucht einen Alias, erhält einen Namen an. Alle Aliase Suchen in der Anwendung.

## <a name="syntax"></a>Syntax

```cpp
HRESULT FindAlias(
   LPCOLESTR     pcstrName,
   IDebugAlias** ppAlias
);
```

```csharp
int FindAlias(
   string          pcstrName,
   out IDebugAlias ppAlias
);
```

#### <a name="parameters"></a>Parameter
 `pcstrName`

 [in] Der Name des Alias gefunden.

 `ppAlias`

 [out] Alias gefunden (sofern vorhanden) dargestellt, durch die [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls gibt `S_FALSE` (wenn der Alias nicht gefunden wird) oder ein Fehlercode.

## <a name="remarks"></a>Hinweise
 Diese Methode initialisiert das Zielobjekt, vor dem Aufruf null; testet dann null-Werte anschließend, um zu bestimmen, und zwar unabhängig davon, ob der Alias gefunden wurde.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)