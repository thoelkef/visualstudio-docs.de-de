---
title: "IScriptEntry::SetItemName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetItemName
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetItemName"
ms.assetid: 9551a7ec-38f8-466a-9722-09367763f380
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetItemName
Legt den Elementnamen fest, der ein `IScriptEntry`\-Objekt identifiziert.  
  
## Syntax  
  
```  
HRESULT SetItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### Parameter  
 `psz`  
 \[in\] Die Adresse eines Puffers, der den Elementnamen enthält.  Der Elementname wird vom Host verwendet, um den Eintrag zu identifizieren.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_FAIL`|Die Methode konnte nicht.|  
  
## Hinweise  
 Für `IScriptEntry`\-Objekte gibt diese Methode `S_OK` zurück.  
  
 Für `IScriptScriptlet`\-Objekte \(die von `IScriptEntry` ableiten\), gibt diese Methode `E_FAIL` zurück.  Für `IScriptScriptlet`\-Objekte wird der Elementname durch [IActiveScriptAuthor::AddScriptlet](../../winscript/reference/iactivescriptauthor-addscriptlet.md) festgelegt und kann nicht geändert werden.  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetItemName](../../winscript/reference/iscriptentry-getitemname.md)