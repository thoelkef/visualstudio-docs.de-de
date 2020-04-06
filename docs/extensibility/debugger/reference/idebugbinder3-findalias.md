---
title: IDebugBinder3::FindAlias | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::FindAlias
helpviewer_keywords:
- IDebugBinder3::FindAlias method
ms.assetid: b8333701-2718-4983-8513-0875fb7cb730
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f0a697e39d21b1c25a98c09ad6cc4837cca7a293
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735864"
---
# <a name="idebugbinder3findalias"></a>IDebugBinder3::FindAlias
Diese Methode sucht einen Alias mit einem Namen. Dadurch werden alle Aliase im Programm durchsucht.

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

## <a name="parameters"></a>Parameter
`pcstrName`\
[in] Name des zu suchenden Alias.

`ppAlias`\
[out] Alias gefunden (falls vorhanden), dargestellt durch die [IDebugAlias-Schnittstelle.](../../../extensibility/debugger/reference/idebugalias.md)

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, `S_OK`kehrt zurück; Andernfalls wird `S_FALSE` zurückgegeben (wenn kein Alias gefunden wird) oder ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Diese Methode initialisiert das Zielobjekt vor dem Aufruf auf NULL. anschließend wird nach einem Nullwert getestet, um festzustellen, ob der Alias gefunden wurde oder nicht.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
