---
title: IDebugArrayField::GetRank | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 33d5118ffa045ccc2315ccb596850be6922fc2ed
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66321688"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ruft den Rang oder die Anzahl der Dimensionen des Arrays ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetRank( 
   DWORD* pdwRank
);
```

```csharp
int GetRank(
   out uint pdwRank
);
```

## <a name="parameters"></a>Parameter
`pdwRank`\
[out] Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Rang eines Arrays entspricht die Anzahl der Dimensionen ab. In C++ und c#, mehrdimensionale Arrays sind wirklich Arrays von Arrays und kann daher nur ein eindimensionales Array betrachtet werden (und die `GetRank` Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], dagegen auf mehrdimensionale Arrays werden anders verarbeitet, und der Rang eines solchen Arrays gibt die Anzahl der Dimensionen (und die `GetRank` Methode wird immer die Anzahl der Dimensionen).

## <a name="see-also"></a>Siehe auch
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)