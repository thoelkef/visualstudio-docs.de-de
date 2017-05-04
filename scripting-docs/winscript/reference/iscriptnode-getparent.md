---
title: "IScriptNode::GetParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetParent"
ms.assetid: 0fb813f6-ab94-46b2-b0cf-ef5d1cd38ae4
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IScriptNode::GetParent
Gibt das `IScriptNode`\-Objekt zurück, das das übergeordnete Element eines Objekts ist.  
  
## Syntax  
  
```  
HRESULT GetParent(  
   IScriptNode       **ppsnParent  
);  
```  
  
#### Parameter  
 `ppsnParent`  
 \[out\] Die Adresse einer Variablen, die einen Zeiger auf die `IScriptNode`\-Schnittstelle der übergeordneten Instanz empfängt.  
  
 Wenn die Klasse `IScriptEntry` oder `IScriptScriptlet` implementiert, wird ein `IScriptNode`\-Objekt zurückgegeben.  
  
 Wenn die Klasse `IScriptNode`\(eine Webseite darstellen\) implementiert, wird NULL zurückgegeben.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)