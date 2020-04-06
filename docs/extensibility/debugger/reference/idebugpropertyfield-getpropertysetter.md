---
title: IDebugPropertyField::GetPropertySetter | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPropertyField::GetPropertySetter
helpviewer_keywords:
- IDebugPropertyField::GetPropertySetter method
ms.assetid: 744d76fd-2bcc-4917-a040-ce4cc714ef61
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 76834b3d4d61f0a58d7a0d2c36f8e30c444ddca2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80720848"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Ruft die Methode ab, die die Eigenschaft festlegt.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetPropertySetter( 
   IDebugMethodField** ppField
);
```

```csharp
int GetPropertySetter(
   out IDebugMethodField ppField
);
```

## <a name="parameters"></a>Parameter
`ppField`\
[out] Gibt ein [IDebugMethodField-Objekt](../../../extensibility/debugger/reference/idebugmethodfield.md) zurück, das die Methode darstellt, die die Eigenschaft festlegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, kehrt S_OK zurück; andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um die Methode abzurufen, die die Eigenschaft abruft, rufen Sie die [GetPropertyGetter-Methode](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
