---
title: "IScriptNode::GetChild | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetChild
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetChild"
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptNode::GetChild
Gibt das untergeordnete Element zurück, das am angegebenen Index im Knoten ist.  
  
## Syntax  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### Parameter  
 `isn`  
 \[in\] Der Index des untergeordneten Elements im übergeordneten.  
  
 `ppsn`  
 \[out\] Die Adresse einer Variablen, die einen Zeiger auf die `IScriptNode`\-Schnittstelle der untergeordneten Instanz empfängt.  
  
 Für `IScriptNode`\-Objekte, die eine Webseite darstellen, gibt dieses Parameters ein Objekt, das einen Skriptblock enthält.  
  
 Für `IScriptEntry`\-Objekte, die einen Skriptblock angeben, gibt dieses Parameters ein Objekt, das eine Funktion angegeben.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Für `IScriptEntry`\-Objekte, die ein Funktionsobjekt und für `IScriptScriptlet`\-Objekte angeben, schlägt diese Methode aus, da keine untergeordneten Einträge gibt.  
  
## Siehe auch  
 [IScriptNode\-Schnittstelle](../../winscript/reference/iscriptnode-interface.md)