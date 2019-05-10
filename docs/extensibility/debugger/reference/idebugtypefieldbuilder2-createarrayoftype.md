---
title: IDebugTypeFieldBuilder2::CreateArrayOfType | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugTypeFieldBuilder2::CreateArrayOfType
- CreateArrayOfType
ms.assetid: 85166ac9-0bff-49a0-b2fd-ca7f7a8eae4b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 545c2cc9565d70ea40d6a38516eac4c03fc3497d
ms.sourcegitcommit: 6196d0b7fdcb08ba6d28a8151ad36b8d1139f2cc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2019
ms.locfileid: "65226251"
---
# <a name="idebugtypefieldbuilder2createarrayoftype"></a>IDebugTypeFieldBuilder2::CreateArrayOfType
Erstellt ein Array des angegebenen Typs und der Größe.

## <a name="syntax"></a>Syntax

```cpp
HRESULT CreateArrayOfType (
   IDebugField*  pTypeField,
   DWORD         rank,
   IDebugField** pArrayOfTypeField
);
```

```csharp
int CreateArrayOfType (
   IDebugField     pTypeField,
   uint            rank,
   out IDebugField pArrayOfTypeField
);
```

## <a name="parameters"></a>Parameter
 `pTypeField`\

 [in] Typ der Elemente, die das Array aufnehmen wird.

 `rank`\

 [in] Anzahl der Elemente im Array.

 `pArrayOfTypeField`\

 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekte, die das neue Array darstellen.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugTypeFieldBuilder2](../../../extensibility/debugger/reference/idebugtypefieldbuilder2.md)