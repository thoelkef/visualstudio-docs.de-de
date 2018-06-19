---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6a00f7019a96696b0c1bde6876697b71d96c253d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31111871"
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
  
#### <a name="parameters"></a>Parameter  
 `pMessageType`  
 [out] Gibt einen Wert aus der [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) -Enumeration, der den Typ der Nachricht beschreibt.  
  
 `pbstrMessage`  
 [out] Die Nachricht zurückgegeben.  
  
 `pdwType`  
 [out] Gibt den Typ des Fehlers, der mit den Konventionen der Win32- `MessageBox` Funktion. Finden Sie unter der [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox) Funktion Einzelheiten.  
  
 `pbstrHelpFileName`  
 [in, out] Gibt den Namen der Hilfedatei zurück. Möglicherweise eine Null (C++) oder ein leerer Wert (c#), wenn keine Hilfedatei vorhanden ist.  
  
 `pdwHelpId`  
 [in, out] Gibt den hilfebezeichner zurück. 0, wenn keine Hilfe kann dieser Nachricht zugeordnet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](/cpp/mfc/reference/cstring-formatting-and-message-box-display#afxmessagebox)