---
title: NAME_MATCH | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- NAME_MATCH
helpviewer_keywords:
- NAME_MATCH enumeration
ms.assetid: 3842c417-a3c9-4259-a05f-52b64b829ef6
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 26666ff9955d7516ff30c7276bfd46e990577e70
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56714828"
---
# <a name="namematch"></a>NAME_MATCH
Wählt den Fall kann Option für den Abgleich von Namen an.

## <a name="syntax"></a>Syntax

```cpp
typedef enum { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
} NAME_MATCH;
```

```csharp
public enum NameMatchOptions { 
   nmNone            = 0,
   nmCaseSensitive   = 1,
   nmCaseInsensitive = 2
}
```

## <a name="members"></a>Member
 NmNone, die keine Optionen angegeben sind.

 NmCaseSensitive gibt an, dass Namen abgeglichen wird Groß-/Kleinschreibung beachtet werden.

 NmCaseInsensitive gibt an, die zu entfernenden Namen sind nicht in der Groß-/Kleinschreibung beachtet.

## <a name="remarks"></a>Hinweise
 Übergeben als Argument für die folgenden Methoden:

-   [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)

-   [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)

-   [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)

-   [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)

## <a name="requirements"></a>Anforderungen
 Header: sh.h

 Namespace: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)
- [GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)
- [EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)
- [GetMethodFieldsByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getmethodfieldsbyname.md)