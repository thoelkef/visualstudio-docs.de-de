---
title: 'IDebugErrorEvent2:: getErrorMessage | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugErrorEvent2::GetErrorMessage
helpviewer_keywords:
- IDebugErrorEvent2::GetErrorMessage
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: c4b25e040fe391b0bfbd05159779096e6bad9951
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183521"
---
# <a name="idebugerrorevent2geterrormessage"></a>IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Gibt Informationen zurück, die die Erstellung einer lesbaren Fehlermeldung ermöglichen.  
  
## <a name="syntax"></a>Syntax  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```csharp  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### <a name="parameters"></a>Parameter  
 `pMessageType`  
 vorgenommen Gibt einen Wert aus der [MessageType](../../../extensibility/debugger/reference/messagetype.md) -Enumeration zurück, der den Typ der Nachricht beschreibt.  
  
 `pbstrErrorFormat`  
 vorgenommen Das Format der abschließenden Meldung für den Benutzer (Weitere Informationen finden Sie unter "Hinweise").  
  
 `hrErrorReason`  
 vorgenommen Der Fehlercode, der in der Meldung angezeigt wird.  
  
 `pdwType`  
 vorgenommen Schweregrad des Fehlers (verwenden Sie die MB_XXX Konstanten für, `MessageBox` z `MB_EXCLAMATION` . b `MB_WARNING` . oder).  
  
 `pbstrHelpFileName`  
 vorgenommen Pfad zu einer Hilfedatei (festgelegt auf einen NULL-Wert, wenn keine Hilfedatei vorhanden ist).  
  
 `pdwHelpId`  
 vorgenommen ID des anzuzeigenden Hilfe Themas (auf 0 festgelegt, wenn kein Hilfethema vorhanden ist).  
  
## <a name="return-value"></a>Rückgabewert  
 Wenn die Ausführung erfolgreich ist, wird `S_OK`, andernfalls ein Fehlercode zurückgegeben.  
  
## <a name="remarks"></a>Bemerkungen  
 Die Fehlermeldung sollte in den Zeilen von formatiert werden `"What I was doing.  %1"` . Wird dann durch den Aufrufer durch die `"%1"` Fehlermeldung ersetzt, die vom Fehlercode abgeleitet wird (der in zurückgegeben wird `hrErrorReason` ). Der-Parameter teilt dem Aufrufer mit, `pMessageType` wie die abschließende Fehlermeldung angezeigt werden soll.  
  
## <a name="see-also"></a>Weitere Informationen  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)
