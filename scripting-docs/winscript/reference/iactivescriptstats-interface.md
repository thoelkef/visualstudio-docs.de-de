---
title: "IActiveScriptStats-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptStats-Schnittstelle"
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScriptStats-Schnittstelle
Ermöglicht einem Host, die Statistik eines laufenden Skripts abzufragen.  Der Host kann diese Informationen verwenden, um zu bestimmen, ob Skript zu lange gedauert hat, um abzuschließen.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IActiveScriptStats`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Gibt eine der Standardskriptstatistik.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Gibt eine benutzerdefinierte Skriptstatistik zurück.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Setzt die Statistik für dieses Skript zurück.|