---
title: CONNECTION_PROTOCOL | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- CONNECTION_PROTOCOL
helpviewer_keywords:
- CONNECTION_PROTOCOL enumeration
ms.assetid: 99df5865-8b36-486d-9f4c-d10ae2bc688a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 29ac287462149a20f52a1affdeab7fa6b8333711
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737645"
---
# <a name="connection_protocol"></a>CONNECTION_PROTOCOL
Gibt das Protokoll an, das für die Kommunikation zwischen einem Debugserver und dem Debugpaket (DE) verwendet wird.

## <a name="syntax"></a>Syntax

```cpp
typedef enum tagCONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
} CONNECTION_PROTOCOL;
```

```csharp
public enum CONNECTION_PROTOCOL {
    CONNECTION_NONE    = 0,
    CONNECTION_UNKNOWN = 1,
    CONNECTION_LOCAL   = 2,
    CONNECTION_PIPE    = 3,
    CONNECTION_TCPIP   = 4,
    CONNECTION_HTTP    = 5,
    CONNECTION_OTHER   = 6
};
```

## <a name="fields"></a>Felder
`CONNECTION_NONE`\
Es wurde keine Verbindung zu einem Server hergestellt.

`CONNECTION_UNKNOWN`\
Es wurde eine Verbindung hergestellt, die jedoch von einem unbekannten Typ ist.

`CONNECTION_LOCAL`\
Die Verbindung erfolgt mit einem lokalen Server.

`CONNECTION_PIPE`\
Die Verbindung erfolgt über eine named pipe.

`CONNECTION_TCPIP`\
Die Verbindung verwendet TCP/IP.

`CONNECTION_HTTP`\
Die Verbindung verwendet HTTP (über einen Webserver).

`CONNECTION_OTHER`\
Es wurde ein anderer Verbindungstyp eingerichtet (dieser Wert wird derzeit nicht verwendet).

## <a name="remarks"></a>Bemerkungen
Diese Werte werden von der [GetConnectionProtocol-Methode](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md) zurückgegeben.

## <a name="requirements"></a>Requirements (Anforderungen)
Kopfzeile: msdbg.h

Namespace: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Weitere Informationen
- [Enumerationen](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [GetConnectionProtocol](../../../extensibility/debugger/reference/idebugcoreserver3-getconnectionprotocol.md)
