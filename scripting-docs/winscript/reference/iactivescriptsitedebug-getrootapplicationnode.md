---
title: "IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptSiteDebug.GetRootApplicationNode
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptSiteDebug::GetRootApplicationNode"
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptSiteDebug::GetRootApplicationNode
Ruft den Anwendungsknoten ab, unter dem Skriptdokumente hinzugefügt werden sollen.  
  
## Syntax  
  
```  
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### Parameter  
 `ppdanRoot`  
 \[out\] Der Debug\- Anwendungsknoten, der Skriptdokumente enthält.  Kann `NULL` sein.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt den Anwendungsknoten zurück, unter dem Skriptdokumente hinzugefügt werden sollen.  Die Methode kann `NULL` für `ppdanRoot` zurückgeben, wenn Skriptdokumente der obersten Ebene sind.  
  
## Siehe auch  
 [IActiveScriptSiteDebug\-Schnittstelle](../../winscript/reference/iactivescriptsitedebug-interface.md)