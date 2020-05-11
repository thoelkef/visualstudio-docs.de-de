---
title: IDebugCustomAttributeQuery2::EnumCustomAttributes | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
helpviewer_keywords:
- IDebugCustomAttributeQuery2::EnumCustomAttributes
ms.assetid: 94bfce74-aa3d-45f0-8e04-5715faf85217
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5b00ead2236a36c2fa12e1ad154b9f853aa2224d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732587"
---
# <a name="idebugcustomattributequery2enumcustomattributes"></a>IDebugCustomAttributeQuery2::EnumCustomAttributes
Ruft einen Enumerator für alle benutzerdefinierten Attribute ab, die diesem Feld zugeordnet sind.

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

## <a name="parameters"></a>Parameter
`ppEnum`\
[out] Gibt ein [IEnumDebugCustomAttributes-Objekt](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) zurück, das die Liste der benutzerdefinierten Attribute darstellt. Andernfalls wird ein NULL-Wert zurückgegeben, wenn keine benutzerdefinierten Attribute vorhanden sind.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, gibt S_OK oder S_FALSE zurück, wenn in diesem Feld keine benutzerdefinierten Attribute vorhanden sind. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein Feld kann mehrere benutzerdefinierte Attribute aufweisen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
