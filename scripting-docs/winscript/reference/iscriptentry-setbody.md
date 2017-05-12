---
title: "IScriptEntry::SetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetBody"
ms.assetid: 719062e4-98e4-4a7b-946d-6e5dbbcc5225
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IScriptEntry::SetBody
Legt den Text fest, der im Text eines `IScriptEntry` Skriptblocks oder des `IScriptScriptlet` Skriptlets ist.  
  
## Syntax  
  
```  
HRESULT SetBody(  
   LPCOLESTR          psz  
);  
```  
  
#### Parameter  
 `psz`  
 \[in\] für einen `IScriptEntry` Skriptblock, `psz` ist der Text, der in den Skripttags eingeschlossen ist.  
  
 Für einen `IScriptEntry`\-Klassenfunktionsblock ist `psz` der Funktionsrumpf.  
  
 Ein Objekt `IScriptScriptlet` \(das von `IScriptEntry` definiert\), ist `psz` der Skripttext des Skriptlets.  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)   
 [IScriptEntry::GetBody](../../winscript/reference/iscriptentry-getbody.md)