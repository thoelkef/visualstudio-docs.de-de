---
title: IDebugAlias::DIspose | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugAlias::Dispose
helpviewer_keywords:
- IDebugAlias::Dispose method
ms.assetid: e84909a4-d378-4f48-bf25-2c014c77c8e3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: df3a2ecc50063df8f90645b9ccaa72754c3728c1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80736554"
---
# <a name="idebugaliasdispose"></a>IDebugAlias::Dispose
Markiert diesen Alias zum Entfernen.

## <a name="syntax"></a>Syntax

```cpp
HRESULT Dispose();
```

```csharp
int Dispose();
```

## <a name="parameters"></a>Parameter
 Keine.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Sobald diese Methode aufgerufen wurde, ist der Alias nicht mehr verfügbar.

## <a name="see-also"></a>Weitere Informationen
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
