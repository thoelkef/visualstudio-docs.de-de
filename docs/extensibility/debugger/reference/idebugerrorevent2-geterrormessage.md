---
title: IDebugErrorEvent2::GetErrorMessage | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4dffd06c7342b77f1e4293d50217a0c6a468bf18
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31110223"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
Gibt Informationen zurück, die zur Erstellung der eine lesbare Fehlermeldung ermöglicht.  
  
## <a name="syntax"></a>Syntax  
  
```cpp  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pMessageType`  
 [out] Gibt einen Wert aus der [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) Enumeration, die den Typ der Nachricht beschreibt.  
  
 `pbstrErrorFormat`  
 [out] Das Format der die endgültige Nachricht an den Benutzer (Details finden Sie unter "Hinweise").  
  
 `hrErrorReason`  
 [out] Der Fehlercode der Nachricht geht.  
  
 `pdwType`  
 [out] Schweregrad des Fehlers (verwenden Sie die Konstanten MB_XXX für `MessageBox`, z. B. `MB_EXCLAMATION` oder `MB_WARNING`).  
  
 `pbstrHelpFileName`  
 [out] Der Pfad zu einer Hilfedatei (festgelegt auf den Wert null, wenn keine Hilfedatei vorhanden ist).  
  
 `pdwHelpId`  
 [out] Die ID des Hilfethemas anzeigen (auf 0, wenn kein Hilfethema festgelegt).  
  
## <a name="return-value"></a>Rückgabewert  
 Im Erfolgsfall gibt `S_OK`ist, andernfalls wird ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Hinweise  
 Die Fehlermeldung formatiert werden sollen, nach dem Vorbild der `"What I was doing.  %1"`. Die `"%1"` würde dann vom Aufrufer mit der Fehlermeldung, abgeleitet aus dem Fehlercode ersetzt (der zurückgegeben wird, `hrErrorReason`). Die `pMessageType` -Parameter weist den Aufrufer wie die endgültigen Fehlermeldung angezeigt werden soll.  
  
## <a name="see-also"></a>Siehe auch  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)