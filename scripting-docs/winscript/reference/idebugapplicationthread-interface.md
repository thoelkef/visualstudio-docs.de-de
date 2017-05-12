---
title: "IDebugApplicationThread-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugApplicationThread-Schnittstelle"
ms.assetid: f869c328-4409-4b74-a6c3-9e63fc58c63d
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugApplicationThread-Schnittstelle
Ermöglicht Sprachmodule und Hosts, die Threadsynchronisierung bereitzustellen und threadspezifische von Zustandsinformationen.  Diese Schnittstelle erweitert die `IRemoteDebugApplicationThread`\-Schnittstelle, um NichtRemote Zugriff auf den Thread zu ermöglichen.  
  
 Zusätzlich zu den von `IRemoteDebugApplicationThread` geerbten Methoden macht die `IDebugApplicationThread`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugApplicationThread::SynchronousCallIntoThread](../../winscript/reference/idebugapplicationthread-synchronouscallintothread.md)|Stellt einen Mechanismus für den Aufrufer um Code im Anwendungsthread bereit.|  
|[IDebugApplicationThread::QueryIsCurrentThread](../../winscript/reference/idebugapplicationthread-queryiscurrentthread.md)|Bestimmt, ob dieser Thread der momentan ausgeführten Thread ist.|  
|[IDebugApplicationThread::QueryIsDebuggerThread](../../winscript/reference/idebugapplicationthread-queryisdebuggerthread.md)|Bestimmt, ob dieser Thread der Debuggerthread ist.|  
|[IDebugApplicationThread::SetDescription](../../winscript/reference/idebugapplicationthread-setdescription.md)|Legt die Beschreibung dieses Threads fest.|  
|[IDebugApplicationThread::SetStateString](../../winscript/reference/idebugapplicationthread-setstatestring.md)|Legt die Beschreibung des Threadzustandes fest.|