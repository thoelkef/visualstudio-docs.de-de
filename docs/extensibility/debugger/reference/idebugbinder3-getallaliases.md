---
title: IDebugBinder3::GetAllAliases | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugBinder3::GetAllAliases
helpviewer_keywords:
- IDebugBinder3::GetAllAliases method
ms.assetid: 1f9ab2ee-2ab3-4a61-8b99-95dd7fdf3511
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2d512fa6eb7529e11c766d7c173b318aa6f8f2f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80735809"
---
# <a name="idebugbinder3getallaliases"></a>IDebugBinder3::GetAllAliases
Diese Methode ruft eine Liste von Aliasnamen aus dem Programm ab.

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

## <a name="parameters"></a>Parameter
`uRequest`\
[in] Die maximale Anzahl der zurückzugebenden Aliase (gibt die `ppAliases`Länge des Arrays an, das an übergeben wird).

`ppAliases`\
[in, out] Array, das mit Aliasen ausgefüllt werden `uRequest` soll (wenn dies ein NULL-Wert ist `puFetched`und 0 ist, wird die Anzahl der Aliase, die zurückgegeben werden können, von zurückgegeben).

`puFetched`\
[out] Gibt die Anzahl der erhaltenen Aliase zurück.

## <a name="return-value"></a>Rückgabewert
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Weitere Informationen
- [IDebugBinder3](../../../extensibility/debugger/reference/idebugbinder3.md)
