---
title: IDebugCustomAttribute::GetAttributeTypeField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
helpviewer_keywords:
- IDebugCustomAttribute::GetAttributeTypeField
ms.assetid: d6ce26d5-42ba-44c1-8659-0516db5bc82d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 51341b3c9b351307d2662538cc3a6797c58b62f9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732784"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Ruft den benutzerdefinierten Attributklassentyp ab.

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

## <a name="parameters"></a>Parameter
`ppCAType`\
[out] Gibt das [IDebugClassField-Objekt](../../../extensibility/debugger/reference/idebugclassfield.md) zurück, das die Klasse darstellt, deren Instanz das benutzerdefinierte Attribut ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode bietet Zugriff auf ein [IDebugClassField-Objekt,](../../../extensibility/debugger/reference/idebugclassfield.md) das diese Klasse beschreibt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
