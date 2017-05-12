---
title: "IDebugSyncOperation-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSyncOperation-Schnittstelle"
ms.assetid: 8d714492-1836-462c-980a-c99e91a2c81b
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSyncOperation-Schnittstelle
Ermöglicht einem Skriptmodul, eine Operation zu extrahieren \(wie Ausdrucksauswertung\) diesen muss ausgeführt werden, während Sie in einer bestimmten geschachtelt werden, blockierte Thread.  Die Schnittstelle stellt auch einen Mechanismus zum Abbrechen von nicht reagierenden Vorgängen bereit.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugSyncOperation`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugSyncOperation::GetTargetThread](../../winscript/reference/idebugsyncoperation-gettargetthread.md)|Gibt den Zielanwendungsthread für diesen Gleichlaufbetrieb zurück.|  
|[IDebugSyncOperation::Execute](../../winscript/reference/idebugsyncoperation-execute.md)|Führt den Vorgang synchron aus und gibt zurück.|  
|[IDebugSyncOperation::InProgressAbort](../../winscript/reference/idebugsyncoperation-inprogressabort.md)|Bricht einen Vorgang ab, der in einem anderen Thread ausgeführt wird.|