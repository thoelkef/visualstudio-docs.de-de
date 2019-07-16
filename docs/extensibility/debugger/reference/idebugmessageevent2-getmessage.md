---
title: IDebugMessageEvent2::GetMessage | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 758b3b860167ed8c2db8bb20c0d76ab289e39a0f
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66346889"
---
# <a name="idebugmessageevent2getmessage"></a>IDebugMessageEvent2::GetMessage
Ruft die Meldung ab, die angezeigt werden.

## <a name="syntax"></a>Syntax

```cpp
HRESULT GetMessage( 
   MESSAGETYPE* pMessageType,
   BSTR*        pbstrMessage,
   DWORD*       pdwType,
   BSTR*        pbstrHelpFileName,
   DWORD*       pdwHelpId
);
```

```csharp
int GetMessage( 
   out enum_MESSAGETYPE pMessageType,
   out string           pbstrMessage,
   out uint             pdwType,
   out string           pbstrHelpFileName,
   out uint             dwHelpId
);
```

## <a name="parameters"></a>Parameter
`pMessageType`\
[out] Gibt einen Wert aus der [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) -Enumeration, der den Typ der Nachricht beschreibt.

`pbstrMessage`\
[out] Die Nachricht zurückgegeben.

`pdwType`\
[out] Gibt den Typ der Nachricht mit den Konventionen der Win32- `MessageBox` Funktion. Finden Sie unter den [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) -Funktion für Details.

`pbstrHelpFileName`\
[in, out] Gibt den Namen der Hilfedatei zurück. Möglicherweise eine (C++) leer oder Null (c#), wenn keine Hilfedatei vorhanden ist.

`pdwHelpId`\
[in, out] Gibt den hilfebezeichner. 0, wenn keine Hilfe kann mit dieser Nachricht zugeordnet werden.

## <a name="return-value"></a>Rückgabewert
 Wenn erfolgreich, wird `S_OK`ist, andernfalls ein Fehlercode zurückgegeben.

## <a name="see-also"></a>Siehe auch
- [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)
- [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
- [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)