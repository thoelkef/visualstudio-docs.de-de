---
title: 'IDebugCustomAttributeQuery2:: iscustomattributedefined | Microsoft-Dokumentation'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80732535"
---
# <a name="idebugcustomattributequery2iscustomattributedefined"></a>IDebugCustomAttributeQuery2::IsCustomAttributeDefined
Bestimmt, ob ein benutzerdefiniertes Attribut anhand des Namens vorhanden ist.

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
in Eine Zeichenfolge mit dem Namen des zu suchenden benutzerdefinierten Attributs.

## <a name="return-value"></a>Rückgabewert
 Gibt S_OK zurück, wenn das benutzerdefinierte Attribut für dieses Feld definiert ist, andernfalls wird S_FALSE zurückgegeben.

## <a name="remarks"></a>Bemerkungen
 Rufen Sie die [GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md) -Methode auf, um die dem benutzerdefinierten Attribut zugeordneten Attribut Bytes zu erhalten.

## <a name="see-also"></a>Weitere Informationen
- [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)
