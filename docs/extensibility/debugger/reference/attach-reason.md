---
title: ATTACH_REASON | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- ATTACH_REASON
helpviewer_keywords:
- ATTACH_REASON enumeration
ms.assetid: 159fb70b-a344-4ba6-9115-b7eaa16e228f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ca871d9dac2b6f37018af925eece5c1a6f3d1585
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80738124"
---
# <a name="attach_reason"></a>ATTACH_REASON
Gibt den Grund für das Anfügen der Debug-Engine (de) an einen Programmknoten an.

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

## <a name="fields"></a>Felder
`ATTACH_REASON_AUTO`\
Anfügen, da sich der Prozess derzeit im Debugmodus befindet.

`ATTACH_REASON_LAUNCH`\
Anfügen, da der Prozess gestartet wurde.

`ATTACH_REASON_USER`\
Anfügen aufgrund einer Benutzer Anforderung.

## <a name="remarks"></a>Bemerkungen
Diese Werte werden als Parameter für die [Anfüge](../../../extensibility/debugger/reference/idebugengine2-attach.md) -und [Anfüge](../../../extensibility/debugger/reference/idebugprogramex2-attach.md) Methoden verwendet.

## <a name="requirements"></a>Anforderungen
Header: msdbg. h

Namespace: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Siehe auch
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugengine2-attach.md)
- [Anfügen](../../../extensibility/debugger/reference/idebugprogramex2-attach.md)
