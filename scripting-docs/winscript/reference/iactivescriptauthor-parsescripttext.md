---
title: "IActiveScriptAuthor::ParseScriptText | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.ParseScriptText
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::ParseScriptText"
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# IActiveScriptAuthor::ParseScriptText
Analysiert das Skript Text, fügen der Text dem Skripterstellungsmodul hinzu und erstellen ein `IScriptEntry`\-Objekt, das dem Skriptblock entspricht.  
  
## Syntax  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### Parameter  
 `pszCode`  
 \[in\] Der analysieren Skripttext.  
  
 `pszItemName`  
 \[in\] Verknüpft die Pufferadresse, die den Elementnamen enthält, mit dem Skriptblock zu.  
  
 `pszDelimiter`  
 \[in\] Die Adresse des Ende\-von\-SkriptBlock Trennzeichens.  Wenn `pszCode` aus einem Stream des Texts analysiert wird, verwendet der Host in der Regel ein Trennzeichen \(wie zwei einfache Anführungszeichen\), um das Ende des Skriptblocks zu erkennen.  Legen Sie diesen Parameter auf fest, um auf NULL, wenn kein Trennzeichen gibt, zum Ende des Skriptblocks zu identifizieren.  
  
 `dwCookie`  
 \[in\] Ein Anwendung festgelegten Wert, der mit dem neuen `IScriptEntry`\-Objekt zugeordnet ist.  
  
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