---
title: IDebugField::GetType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetType
helpviewer_keywords:
- IDebugField::GetType method
ms.assetid: b3cdec9f-ef7b-44d0-a775-d17ef7eae968
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8887be18d59d331913a1978d915b91f9c996b8f0
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919506"
---
# <a name="idebugfieldgettype"></a>IDebugField::GetType
Diese Methode ruft den Typ des Felds ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetType( 
   IDebugField** ppType
);
```

```csharp
int GetType(
   out IDebugField ppType
);
```

#### <a name="parameters"></a>Parameter
 `ppType`

 [out] Gibt den Feldtyp, wie eine andere [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)