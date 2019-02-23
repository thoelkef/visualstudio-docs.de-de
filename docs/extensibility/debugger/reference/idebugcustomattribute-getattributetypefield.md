---
title: IDebugCustomAttribute::GetAttributeTypeField | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cbbf0d91b344f1a45eb09d480eb631ac1a159046
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56722784"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Ruft ab, der Typ des benutzerdefinierten Attributs-Klasse.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetAttributeTypeField( 
   IDebugClassField** ppCAType
);
```

```csharp
int GetAttributeTypeField(
   out IDebugClassField ppCAType
);
```

#### <a name="parameters"></a>Parameter
 `ppCAType`

 [out] Gibt die [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das die Klasse darstellt, von denen das benutzerdefinierte Attribut eine Instanz ist.

## <a name="return-value"></a>Rückgabewert
 Im Erfolgsfall gibt S_OK zurück. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Hinweise
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode ermöglicht den Zugriff auf eine [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) Objekt, das diese Klasse beschreibt.

## <a name="see-also"></a>Siehe auch
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)