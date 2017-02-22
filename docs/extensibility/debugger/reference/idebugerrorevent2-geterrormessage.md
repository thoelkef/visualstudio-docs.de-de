---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Gibt Informationen zurück, die die Konstruktion einer lesbaren Fehlermeldung zulässig.  
  
## Syntax  
  
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
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### Parameter  
 `pMessageType`  
 \[out\]  Gibt einen Wert aus der [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)\-Enumeration zurück und beschreibt den Typ der Meldung.  
  
 `pbstrErrorFormat`  
 \[out\]  Das Format der letzten Meldung für den Benutzer finden Sie im Abschnitt „Hinweise“ \(Details\).  
  
 `hrErrorReason`  
 \[out\]  Der Fehlercode ist ungefähr der Meldung.  
  
 `pdwType`  
 \[out\]  Schweregrad des Fehlers \(verwenden Sie die MB\_XXX\-Konstanten für `MessageBox`. `MB_EXCLAMATION` oder z. B. `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[out\]  Pfad zu einer Hilfedatei \(mit einem NULL\-Wert, wenn keine Hilfedatei vorhanden ist\).  
  
 `pdwHelpId`  
 \[out\]  ID des anzuzeigenden Hilfethemas \(auf 0 festgelegt, wenn kein Hilfethema vorhanden ist\).  
  
## Rückgabewert  
 Bei Erfolg gibt `S_OK`zurück. andernfalls gibt einen Fehlercode zurück.  
  
## Hinweise  
 Die Fehlermeldung sollte nach den Grundsätzen von `"What I was doing.  %1"`formatiert werden.  `"%1"` würde dann vom Aufrufer über die Fehlermeldung ersetzt, die vom Fehlercode abgeleitet wurde \(der in `hrErrorReason`zurückgegeben wurde\).  Der `pMessageType`\-Parameter weist den Aufrufer, wie die letzte Fehlermeldung angezeigt werden soll.  
  
## Siehe auch  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)