---
title: "IScriptEntry::GetBody | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetBody
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetBody"
ms.assetid: 419c8c11-a1f8-4b97-ab00-e8af2b2f9bfc
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetBody
Gibt den Text zurück, der dem Text eines `IScriptEntry` Skriptblocks, des Funktionsblocks oder des Skriptlets entspricht.  
  
## Syntax  
  
```  
HRESULT GetBody(  
   BSTR               *pbstr  
);  
```  
  
#### Parameter  
 `pbstr`  
 \[out\] Der Text, der im Text eines der folgenden ist:  
  
-   Ein `IScriptEntry` Skriptblock  
  
-   Eine `IScriptEntry`\-Funktion in einem Klassenfunktionsblock  
  
-   Ein `IScriptEntry` Skriptletereignishandler  
  
## Rückgabewert  
 Ein `HRESULT`.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
  
## Siehe auch  
 [IScriptEntry\-Schnittstelle](../../winscript/reference/iscriptentry-interface.md)