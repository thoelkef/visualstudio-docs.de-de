---
title: "IActiveScriptAuthor::GetEventHandler | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetEventHandler
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetEventHandler"
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IActiveScriptAuthor::GetEventHandler
Gibt das Skriptlet zurück, das die angegebenen Attribute verfügt.  
  
## Syntax  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### Parameter  
 `pdisp`  
 \[in\] Das `IDispatch`\-Objekt, das zum `NamedItem` entspricht, in denen das Skriptlet angefügt wird.  
  
 `pszItem`  
 \[in\] Die Pufferadresse des Bezeichners der obersten Ebene des vollqualifizierten Skriptletnamens im Host.  
  
 `pszSubItem`  
 \[in\] Die Pufferadresse des Bezeichners der zweiten Ebene des vollqualifizierten Skriptletnamens im Host.  Legen Sie den auf NULL, wenn der Name nur eine Ebene verfügt.  
  
 `pszEvent`  
 \[in\] Die Adresse eines Puffers, der den Ereignisnamen enthält.  Das Skriptlet ist ein Ereignishandler für dieses Ereignis.  
  
 `ppse`  
 \[out\] Die Adresse einer Variablen, die einen Zeiger auf die `IScriptEntry`\-Schnittstelle des Skriptlets empfängt, das die angegebenen Attribute verfügt.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)