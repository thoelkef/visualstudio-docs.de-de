---
title: "IActiveScriptAuthor::AddScriptlet | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddScriptlet
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddScriptlet"
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IActiveScriptAuthor::AddScriptlet
Fügt ein Codeskriptlet als untergeordnetes Element des `IScriptNode`\-Stammebenenobjekts hinzu.  Im Host wird dem vollqualifizierten Namen des Skriptlets ermöglicht, nur zwei Ebenen zu haben.  
  
## Syntax  
  
```  
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parameter  
 `pszDefaultName`  
 \[in\] Die Adresse des mit dem Skriptlet zuzuordnen, bei.  
  
 `pszCode`  
 \[in\] Die Adresse des Skriptlettexts.  
  
 `pszItemName`  
 \[in\] Die Pufferadresse des Bezeichners der obersten Ebene des vollqualifizierten Skriptletnamens im Host.  
  
 `pszSubItemName`  
 \[in\] Die Pufferadresse des Bezeichners der zweiten Ebene des vollqualifizierten Skriptletnamens im Host.  Legen Sie den auf NULL, wenn der Name nur eine Ebene verfügt.  
  
 `pszEventName`  
 \[in\] Die Adresse eines Puffers, der den Ereignisnamen enthält, für den das Skriptlet ein Ereignishandler ist.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-von\-SkriptBlock Trennzeichens.  Wenn `pszCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptblocks zu erkennen.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn ein Trennzeichen nicht das Ende des Skriptblocks markiert.  
  
 `dwCookie`  
 \[in\] Ein Anwendung festgelegten Wert, der verwendet wird, um das Skriptlet mit einem Hostobjekt zuzuordnen.  
  
 `dwFlags`  
 \[in\] Wird nicht verwendet.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)