---
title: 'Idebugobject:: SetValue | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject::SetValue
helpviewer_keywords:
- IDebugObject::SetValue method
ms.assetid: d652e09c-cdc1-4519-8116-d7c743f5679b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 9e4652eb3c77a1871063dfa71b464fb1f7c43f94
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80726368"
---
# <a name="idebugobjectsetvalue"></a>IDebugObject::SetValue
Legt den Wert des-Objekts aus einer aufeinanderfolgenden Reihe von Bytes fest.

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

## <a name="parameters"></a>Parameter
`pValue`\
in Ein Bytearray, das den neuen Wert darstellt.

`nSize`\
in Die Größe des Werts in Bytes.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Die Werte im Array werden in dieses [idebugobject](../../../extensibility/debugger/reference/idebugobject.md) -Objekt kopiert, wobei ein beliebiger vorhandener Wert ersetzt wird. Die Größe des neuen Werts kann größer oder kleiner als der vorhandene Wert sein. Dies `IDebugObject` darf kein NULL-Verweis sein.

## <a name="see-also"></a>Weitere Informationen
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)
