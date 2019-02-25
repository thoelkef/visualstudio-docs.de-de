---
title: IDebugArrayField::GetRank | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1c091c7696867f369262a81259105dcf23fbe4c9
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56698156"
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

#### <a name="parameters"></a>Parameter
 `pdwRank`

 [out] Gibt den Rang zurück.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Der Rang eines Arrays entspricht die Anzahl der Dimensionen ab. In C++ und c#, mehrdimensionale Arrays sind wirklich Arrays von Arrays und kann daher nur ein eindimensionales Array betrachtet werden (und die `GetRank` Methode gibt immer 1 zurück). In [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], dagegen auf mehrdimensionale Arrays werden anders verarbeitet, und der Rang eines solchen Arrays gibt die Anzahl der Dimensionen (und die `GetRank` Methode wird immer die Anzahl der Dimensionen).

## <a name="see-also"></a>Siehe auch
- [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)