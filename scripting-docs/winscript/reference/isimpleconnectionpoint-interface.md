---
title: "ISimpleConnectionPoint-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "ISimpleConnectionPoint-Schnittstelle"
ms.assetid: f632a82f-942d-4291-963e-e9fa2b162493
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# ISimpleConnectionPoint-Schnittstelle
Stellt eine einfache Möglichkeit zum Beschreiben und Auflisten der Ereignisse bereit, die auf einem bestimmten Verbindungspunkt ausgelöst werden.  Diese Schnittstelle macht es auch einfach, in ein Objekt `IDispatch` für diese Ereignisse zu verknüpfen.  Diese Schnittstelle wird vom Prozessdebug\-Manager \(PDM\) implementiert und verwendet durch Skriptmodule.  
  
 Diese Schnittstelle ist von `IDebugHelper::CreateSimpleConnectionPoint` verfügbar.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `ISimpleConnectionPoint`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[ISimpleConnectionPoint::Advise](../../winscript/reference/isimpleconnectionpoint-advise.md)|Richtet eine Verbindung zwischen dem einfachen Verbindungspunktobjekt und der Senke des Clients ein.|  
|[ISimpleConnectionPoint::DescribeEvents](../../winscript/reference/isimpleconnectionpoint-describeevents.md)|Gibt den DISPID und den Namen für jedes Ereignis in einem angegebenen Bereich von Ereignissen zurück.|  
|[ISimpleConnectionPoint::GetEventCount](../../winscript/reference/isimpleconnectionpoint-geteventcount.md)|Gibt die Anzahl von Ereignissen zurück, die auf dieser Schnittstelle verfügbar gemacht werden.|  
|[ISimpleConnectionPoint::Unadvise](../../winscript/reference/isimpleconnectionpoint-unadvise.md)|Beendet eine Advise\-Verbindung, die zuvor mit `ISimpleConnectionPoint::Advise` eingerichtet wurde.|  
  
## Siehe auch  
 [IDebugProperty\-Schnittstelle](../../winscript/reference/idebugproperty-interface.md)