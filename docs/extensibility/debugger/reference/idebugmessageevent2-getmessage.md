---
title: IDebugMessageEvent2::GetMessage | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugMessageEvent2::GetMessage
helpviewer_keywords:
- GetMessage method
- IDebugMessageEvent2::GetMessage method
ms.assetid: 9fca7285-f7f1-422d-8565-92bf0e0db60a
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 190d4dab907e1c0934cb91f7fef6f87989569cad
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

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
 [out] Gibt den Typ des Fehlers, der mit den Konventionen der Win32- `MessageBox` Funktion. Finden Sie unter der [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8) Funktion Einzelheiten.  
  
 `pbstrHelpFileName`  
 [in, out] Gibt den Namen der Hilfedatei zurück. Möglicherweise eine Null (C++) oder ein leerer Wert (c#), wenn keine Hilfedatei vorhanden ist.  
  
 `pdwHelpId`  
 [in, out] Gibt den hilfebezeichner zurück. 0, wenn keine Hilfe kann dieser Nachricht zugeordnet werden.  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)   
 [AfxMessageBox](http://msdn.microsoft.com/Library/d66d0328-cdcc-48f6-96a4-badf089099c8)
