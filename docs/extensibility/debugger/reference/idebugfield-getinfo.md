---
title: IDebugField::GetInfo | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugField::GetInfo
helpviewer_keywords:
- IDebugField::GetInfo method
ms.assetid: 7d508200-89ce-400f-a8ea-f28e7610cb2b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 53c0de1b956202f95b4995855ec5bdda0ebe59d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66352629"
---
# <a name="idebugfieldgetinfo"></a>IDebugField::GetInfo
Diese Methode ruft die anzeigbare Informationen über das Feld ab.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetInfo( 
   FIELD_INFO_FIELDS dwFields,
   FIELD_INFO* pFieldInfo
);
```

```csharp
int GetInfo(
   enum_FIELD_INFO_FIELDS dwFields,
   FIELD_INFO[] pFieldInfo
);
```

## <a name="parameters"></a>Parameter
`dwFields`\
[in] Eine Kombination von [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) Konstanten, die die Informationen, die angezeigt wird, werden ausgewählt. Wenn das Feld ein Symbol darstellt, ist dies in der Regel den Symbolnamen und Typ.

`pFieldInfo`\
[out] Gibt Informationen zurück, in der angegebenen [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) Struktur.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)