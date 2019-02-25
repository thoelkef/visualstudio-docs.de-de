---
title: GETHOSTNAME_TYPE | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- GETHOSTNAME_TYPE
helpviewer_keywords:
- GETHOSTNAME_TYPE enumeration
ms.assetid: 2be92bea-8133-412b-9015-1833baf16e1b
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d8578056f907c70e3b900b1f3cdbcbeefc39688b
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689237"
---
# <a name="gethostnametype"></a>GETHOSTNAME_TYPE
Gibt den Typ des Hostnamens.

## <a name="syntax"></a>Syntax

```cpp
enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
typedef DWORD GETHOSTNAME_TYPE;
```

```csharp
public enum enum_GETHOSTNAME_TYPE {
    GHN_FRIENDLY_NAME = 0,
    GHN_FILE_NAME     = 1
};
```

## <a name="members"></a>Member
GHN_FRIENDLY_NAME gibt einen Anzeigenamen des Hosts an.

GHN_FILE_NAME gibt einen Dateinamen des Hosts an.

## <a name="remarks"></a>Hinweise
Diese Werte werden übergeben, als Argument an die [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md) Methode, um einen Hostnamen in verschiedenen Formaten abzurufen.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetHostName](../../../extensibility/debugger/reference/idebugprogramnode2-gethostname.md)
