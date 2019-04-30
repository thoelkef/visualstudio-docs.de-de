---
title: IDebugPointerField::GetDereferencedField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 51ddd954e069ae2f6a683b727305808b8591d4f2
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62872042"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
Diese Methode gibt den Typ des Objekts, die auf den dieser Zeiger-Objekt verweist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetDereferencedField(
   IDebugField** ppField
);
```

```csharp
int GetDereferencedField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parameter
 `ppField`

 [out] Gibt eine [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) beschreibt den Typ des Zielobjekts.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn z. B. die [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md) -Objekt verweist auf eine ganze Zahl, die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) von dieser Methode zurückgegebene Typ beschreibt, Integer-Datentyp.

## <a name="see-also"></a>Siehe auch
- [IDebugPointerField](../../../extensibility/debugger/reference/idebugpointerfield.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)