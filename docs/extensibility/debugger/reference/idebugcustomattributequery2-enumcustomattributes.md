---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aade3935a49af176220e800647e6e821054bbb48
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710356"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Ruft einen Enumerator für alle benutzerdefinierten Attribute, die an dieses Feld angefügt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT EnumCustomAttributes( 
   IEnumDebugCustomAttributes** ppEnum
);
```

```csharp
int EnumCustomAttributes(
   out IEnumDebugCustomAttributes ppEnum
);
```

#### <a name="parameters"></a>Parameter
 `ppEnum`

 [out] Gibt eine [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) Objekt, das die Liste der benutzerdefinierten Attribute darstellt; andernfalls einen null-Wert, wenn keine benutzerdefinierten Attribute vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück, oder S_FALSE zurück, wenn keine benutzerdefinierten Attribute für dieses Feld vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben;

## <a name="remarks"></a>Hinweise
 Ein Feld kann mehrere benutzerdefinierte Attribute aufweisen.

## <a name="see-also"></a>Siehe auch
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)