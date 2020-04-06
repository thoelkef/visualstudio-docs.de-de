---
title: IDebugCustomAttributeQuery2::IsCustomAttributeDefined | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
helpviewer_keywords:
- IDebugCustomAttributeQuery2::IsCustomAttributeDefined
ms.assetid: 5c07cc52-6d2d-42df-9d76-9f1f769641db
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 7be649a5d65f88d8263bbe8950fda1a157855ed2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732535"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Bestimmt, ob ein benutzerdefiniertes Attribut nach Namen vorhanden ist.

## <a name="syntax"></a>Syntax

```cpp
HRESULT IsCustomAttributeDefined( 
   LPCOLESTR pszCustomAttributeName
);
```

```csharp
int IsCustomAttributeDefined(
   [In] string pszCustomAttributeName
);
```

## <a name="parameters"></a>Parameter
`pszCustomAttributeName`\
[in] Eine Zeichenfolge, die den Namen des zu suchenden benutzerdefinierten Attributs enthält.

## <a name="return-value"></a>Rückgabewert
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für dieses Feld definiert ist, andernfalls wird S_FALSE zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Um die Attributbytes zu erhalten, die dem benutzerdefinierten Attribut zugeordnet sind, rufen Sie die [GetCustomAttributeByName-Methode](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) auf.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
