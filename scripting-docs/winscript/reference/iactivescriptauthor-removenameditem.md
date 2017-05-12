---
title: "IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveNamedItem"
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::RemoveNamedItem
Entfernt ein `NamedItem`\-Objekts im Namespace des Skripterstellungsmoduls.  
  
## Syntax  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### Parameter  
 `pszName`  
 \[in\] Die Adresse des Puffers, der das Objekt identifiziert `NamedItem`, um zu entfernen.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`S_FALSE`|Das Objekt ist nicht `NamedItem` im Namespace des Skripterstellungsmoduls vorhanden.|  
  
## Hinweise  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) wird verwendet, um das `NamedItem`\-Objekt in den Namespace des Skripterstellungs\-Moduls einzufügen.  
  
## Siehe auch  
 [IActiveScriptAuthor\-Schnittstelle](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)