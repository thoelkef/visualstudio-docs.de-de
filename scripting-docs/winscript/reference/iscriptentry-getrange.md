---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
Gibt die Anfangsposition und die Länge eines Eintrags zurück.  
  
## Syntax  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### Parameter  
 `pichMin`  
 \[out\] für `IScriptEntry`\-Objekte, die einen Skriptblock angeben, gibt 0 zurück.  
  
 Für `IScriptEntry`\-Objekte, die ein Funktionsobjekt angeben, gibt die Anfangsposition der Funktion im aktuellen Skriptblock.  
  
 Für `IScriptScriptlet`\-Objekte gibt 0 zurück.  
  
 `pcch`  
 \[out\] für `IScriptEntry`\-Objekte, die einen Skriptblock angeben, gibt die Länge des Texts.  
  
 Für `IScriptEntry`\-Objekte, die ein Funktionsobjekt angeben, gibt die Länge der Funktionsdefinition.  
  
 Für `IScriptScriptlet`\-Objekte gibt die Länge des Eintrags.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)