---
title: IDebugBinder3::GetAllAliases | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ed8545431dc0cb643ba18d415285447f8a66f66e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62923704"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Diese Methode ruft eine Liste der Aliase ab, aus dem Programm.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAllAliases(
   UINT          uRequest,
   IDebugAlias** ppAliases,
   UINT*         puFetched
);
```

```csharp
int GetAllAliases(
   uint          uRequest,
   IDebugAlias[] ppAliases,
   out uint      puFetched
);
```

#### <a name="parameters"></a>Parameter
 `uRequest`

 [in] Die maximale Anzahl von Aliasen zu zurückgeben (gibt die Länge des übergebenen Arrays `ppAliases`).

 `ppAliases`

 [in, out] Mit Aliasen auszufüllende Array (ist dies ein null-Wert und `uRequest` gleich 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, zurückgegeben werden, indem `puFetched`).

 `puFetched`

 [out] Gibt die Anzahl von Aliasen abgerufen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)