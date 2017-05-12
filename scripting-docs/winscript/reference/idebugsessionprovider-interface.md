---
title: "IDebugSessionProvider-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IDebugSessionProvider-Schnittstelle"
ms.assetid: 1b898423-7af9-44f5-8dda-987005309c99
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugSessionProvider-Schnittstelle
Die primäre Schnittstelle, die von einem Debugger IDE bereitgestellt wurde, um Host und Sprache zu aktivieren, Debuggen initiiert hat.  Sie legt eine Debugsitzung für eine laufende Anwendung ein.  Diese Schnittstelle wird vom Computer Debug\- Manager implementiert.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugSessionProvider`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugSessionProvider::StartDebugSession](../../winscript/reference/idebugsessionprovider-startdebugsession.md)|Initiiert eine Debugsitzung mit der angegebenen Anwendung.|