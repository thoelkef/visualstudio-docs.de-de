---
title: "IActiveScriptStats::GetStat | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptStats.GetStat
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptStats::GetStat"
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats::GetStat
Gibt eine der Standardskriptstatistik.  
  
## Syntax  
  
```  
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### Parameter  
 `stid`  
 \[in\] Gibt an, das die Statistik zurückgegeben.  Muss der Wert:  
  
|Konstante|Wert|Description|  
|---------------|----------|-----------------|  
|SCRIPTSTAT\_STATEMENT\_COUNT|1|Geben Sie die Anzahl der Anweisungen zurück, die ausgeführt werden, da das begonnene Skript oder die Statistik zurückgesetzt wurde.|  
  
 `pluHi`  
 \[out\] Die Bits des Wichtigkeitswert 32 eine 64\-Bit\-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
 `pluLo`  
 \[out\] Die Bits des Tiefs 32 eine 64\-Bit\-Ganzzahl ohne Vorzeichen, die die Statistik darstellt.  
  
## Rückgabewert  
 Die Methode gibt ein `HRESULT` zurück.  Zu den möglichen Werten zählen, aber nicht auf Werte in der folgenden Tabelle beschränkt.  
  
|Wert|Description|  
|----------|-----------------|  
|`S_OK`|Die Methode war erfolgreich.|  
  
## Hinweise  
 Diese Methode gibt ein der Standardskriptstatistik zurück.  
  
## Siehe auch  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [IActiveScriptStats\-Schnittstelle](../../winscript/reference/iactivescriptstats-interface.md)