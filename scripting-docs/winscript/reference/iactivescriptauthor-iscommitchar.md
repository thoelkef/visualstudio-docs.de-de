---
title: "IActiveScriptAuthor::IsCommitChar | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.IsCommitChar
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::IsCommitChar"
ms.assetid: 7857c6f9-61e6-41e5-8e01-f56588c10421
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IActiveScriptAuthor::IsCommitChar
Gibt einen Wert zurück, der angibt, ob ein bestimmtes Zeichen einen Anweisungsvervollständigungscommit durch die Anwendung starten soll.  
  
## Syntax  
  
```  
HRESULT IsCommitChar(  
   OLECHAR    ch,  
   BOOL       *pfcommit  
);  
```  
  
#### Parameter  
 `ch`  
 \[in\] Das Zeichen zu testen.  
  
 `pfcommit`  
 \[out\] `True`, wenn das Zeichen ein Commitzeichen ist; andernfalls `False`.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)