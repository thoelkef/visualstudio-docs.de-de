---
title: "IActiveScriptStats::GetStatEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStatEx
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStatEx"
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStatEx
Gibt eine benutzerdefinierte Skriptstatistik zurück.  
  
## Syntax  
  
```  
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### Parameter  
 `guid`  
 \[in\] Gibt an, das die Statistik zurückgegeben.  Die Semantik, von der Statistiken zu einem bestimmten GUID entspricht, ist vollständig das definierte Modul.  
  
 `pluHi`  
 \[out\] Die Bits des Wichtigkeitswert 32 eine 64\-Bit\-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 \[out\] Die Bits des Tiefs 32 eine 64\-Bit\-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht zu, die in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
|`E_NOTIMPL`|Die Methode ist nicht implementiert.|  
  
## Hinweise  
 Diese Methode ermöglicht ein benutzerdefiniertes Skriptmodul zur Rückholstatistik, die einem benutzerdefinierten Host sinnvoll ist.  
  
> [!NOTE]
>  Diese Methode ist zurzeit nicht implementiert.  
  
## Siehe auch  
 [IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)   
 [IActiveScriptStats\-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)