---
title: IDebugField::GetContainer | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetContainer
helpviewer_keywords:
- IDebugField::GetContainer method
ms.assetid: 6d6c8213-6181-4adf-9584-3e4cac163dd8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 08ce207a4961ed9345c46ca7d19390647dc514b1
ms.sourcegitcommit: 19ec963ed6d585719cb83ba677434ea6580e0d1f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2019
ms.locfileid: "66212275"
---
# <a name="idebugfieldgetcontainer"></a>IDebugField::GetContainer
Diese Methode ruft den Container eines Felds ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetContainer( 
   IDebugContainerField** ppContainerField
);
```

```csharp
int GetContainer(
   out IDebugContainerField ppContainerField
);
```

## <a name="parameters"></a>Parameter
`ppContainerField`\
[out] Gibt den Container zurück, dargestellt durch die [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) Schnittstelle.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Wenn dieses Feld keinen Container, den zurückgegebenen verfügt `ppContainerField` ein null-Wert.

## <a name="see-also"></a>Siehe auch
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)