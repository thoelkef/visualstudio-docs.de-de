---
title: "IDebugThreadCall-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugThreadCall-Schnittstelle"
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugThreadCall-Schnittstelle
Die `IDebugThreadCall`\-Schnittstelle wird in der Regel durch eine Komponente implementiert, die bestimmte Aufrufe mit `IDebugThread` macht, das die Implementierung marshallt, die von bereitgestellt wird, verarbeiten Debug\- Manager \(PDM\).  
  
 Das PDM ruft die `IDebugThreadCall`\-Schnittstelle im gewünschten Thread an, und die `IDebugThreadCall`\-Schnittstelle stellt den Aufruf an der gewünschten Implementierung aus.  Die `IDebugThreadCall`\-Schnittstelle wandelt die Parameterinformationen um, die in die Parameter der entsprechenden Rand übergeben werden.  
  
 Die `IDebugThreadCall`\-Schnittstelle ist ein Freethreadobjekt.  
  
## Methoden  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugThreadCall`\-Schnittstelle die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Handleaufrufe um Code in einem anderen Thread.|