---
title: ATTACH_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7acd5b87288365cde43b2eb8f460b52048dcf36f
ms.sourcegitcommit: 752f03977f45169585e407ef719450dbe219b7fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2019
ms.locfileid: "56318706"
---
# <a name="attachreason"></a>ATTACH_REASON
Gibt den Grund für die Debug-Engine (DE) Verbindung mit einem Programm-Knoten.

## <a name="syntax"></a>Syntax

```cpp
enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
typedef DWORD ATTACH_REASON;
```

```csharp
public enum enum_ATTACH_REASON {
    ATTACH_REASON_LAUNCH = 0x0001,
    ATTACH_REASON_USER   = 0x0002,
    ATTACH_REASON_AUTO   = 0x0003
};
```

## <a name="members"></a>Member
ATTACH_REASON_AUTO  
Angefügt werden, da der Prozess derzeit im Debugmodus befindet.

ATTACH_REASON_LAUNCH  
Angefügt werden, da der Prozess gestartet wurde.

ATTACH_REASON_USER  
Fügen Sie aufgrund einer benutzeranforderung.

## <a name="remarks"></a>Hinweise
Diese Werte werden verwendet, als Parameter an die [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md) und [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methoden.

## <a name="requirements"></a>Anforderungen
Header: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
[Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)  
[Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)  
[Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
