---
title: IDebugObject::SetValue | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ccfea65f7f24b3d48fc5ec5d68028c72b9b4eece
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56692649"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Legt den Wert des Objekts aus eine aufeinanderfolgende Reihe von Bytes fest.

## <a name="syntax"></a>Syntax

```cpp
HRESULT SetValue( 
   BYTE* pValue,
   UINT  nSize
);
```

```csharp
int SetValue(
   byte[] pValue,
   uint   nSize
);
```

#### <a name="parameters"></a>Parameter
 `pValue`

 [in] Ein Array von Bytes, die den neuen Wert darstellt.

 `nSize`

 [in] Die Größe des Werts in Bytes.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Die Werte im Array werden in diese kopiert [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt, und Ersetzen Sie dabei alle vorhandenen Werte. Die Größe des neuen Werts kann größer oder kleiner als der vorhandene Wert sein. Dies `IDebugObject` ein null-Verweis nicht möglich.

## <a name="see-also"></a>Siehe auch
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)