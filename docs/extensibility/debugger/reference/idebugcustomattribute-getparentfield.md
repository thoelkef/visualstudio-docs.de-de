---
title: IDebugCustomAttribute::GetParentField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetParentField
helpviewer_keywords:
- IDebugCustomAttribute::GetParentField
ms.assetid: bcdfdf37-bfcf-4988-a7b8-4c731d0af1b0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 158887e9f2d7d7b250b435570d6780e460508816
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693372"
---
# <a name="idebugcustomattributegetparentfield"></a>IDebugCustomAttribute::GetParentField
Ruft das Feld, das an dem das benutzerdefinierte Attribut angefügt ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetParentField( 
   IDebugField** ppField
);
```

```csharp
int GetParentField(
   out IDebugField ppField
);
```

#### <a name="parameters"></a>Parameter
 `ppField`

 [out] Gibt die [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) -Objekt, das Feld darstellt, an dem das benutzerdefinierte Attribut angefügt ist.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Rufen Sie die [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) Methode für das zurückgegebene [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) Objekt, um zu bestimmen, welche Art von das übergeordnete Feld ist.

## <a name="see-also"></a>Siehe auch
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)