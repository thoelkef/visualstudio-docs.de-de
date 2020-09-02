---
title: 'Idebugpropertyfield:: getpropertysetter | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80720848"
---
# <a name="idebugpropertyfieldgetpropertysetter"></a>IDebugPropertyField::GetPropertySetter
Ruft die Methode ab, die die-Eigenschaft festlegt.

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
vorgenommen Gibt ein [idebugmethodfield](../../../extensibility/debugger/reference/idebugmethodfield.md) -Objekt zurück, das die Methode darstellt, die die-Eigenschaft festlegt.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird S_OK zurückgegeben. Andernfalls wird ein Fehlercode zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um die Methode abzurufen, die die Eigenschaft abruft, können Sie die [getpropertygetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md) -Methode aufrufen.

## <a name="see-also"></a>Weitere Informationen
- [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md)
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [GetPropertyGetter](../../../extensibility/debugger/reference/idebugpropertyfield-getpropertygetter.md)
