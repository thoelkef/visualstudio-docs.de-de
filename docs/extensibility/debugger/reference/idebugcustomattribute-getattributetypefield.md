---
title: 'Idebugcustomattribute:: getattributetypefield | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732784"
---
# <a name="idebugcustomattributegetattributetypefield"></a>IDebugCustomAttribute::GetAttributeTypeField
Ruft den Typ der benutzerdefinierten Attribut Klasse ab.

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
vorgenommen Gibt das [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt zurück, das die Klasse darstellt, von der das benutzerdefinierte Attribut eine Instanz ist.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Ein benutzerdefiniertes Attribut ist immer eine Klasse. Diese Methode ermöglicht den Zugriff auf ein [idebugclassfield](../../../extensibility/debugger/reference/idebugclassfield.md) -Objekt, das diese Klasse beschreibt.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
