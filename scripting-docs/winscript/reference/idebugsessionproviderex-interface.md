---
title: "IDebugSessionProviderEx-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 26c5da2d-8c93-4d2b-94d2-97aaa377dcfe
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDebugSessionProviderEx-Schnittstelle
Die primäre Schnittstelle kann von einem Debugger IDE bereit, um Hauptrechner zu aktivieren und Sprache\-initiierte Debuggen.  Sie legt eine Debugsitzung für eine laufende Anwendung ein.  Diese Schnittstelle wird vom Debuggen Machine Manager implementiert.  
  
 Zusätzlich zu den von `IUnknown` geerbten Methoden macht die `IDebugSessionProviderEx`\-Schnittstelle die folgenden Methoden verfügbar.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IDebugSessionProviderEx:CanJITDebug](../../winscript/reference/idebugsessionproviderex-canjitdebug.md)|Bestimmt, ob Just\-in\-timedebugging mit der angegebenen Anwendung möglich ist.|  
|[IDebugSessionProviderEx:StartDebugSession](../../winscript/reference/idebugsessionproviderex-startdebugsession.md)|Initiiert eine Debugsitzung mit der angegebenen Anwendung.|