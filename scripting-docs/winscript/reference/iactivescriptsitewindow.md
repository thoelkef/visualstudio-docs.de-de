---
title: "IActiveScriptSiteWindow | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IActiveScriptSiteWindow-Schnittstelle"
ms.assetid: 96d5c493-2c0b-47e2-848b-4a8dacdcd65c
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IActiveScriptSiteWindow
Diese Schnittstelle wird von Hosts implementiert, die eine Benutzeroberfläche für das gleiche Objekt wie [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) unterstützen.  Hosts, die keine Benutzeroberfläche, wie Server unterstützen, werden nicht die `IActiveScriptSiteWindow`\-Schnittstelle implementieren.  Das Skriptmodul greift auf diese Schnittstelle zu, indem `QueryInterface` von `IActiveScriptSite` aufruft.  
  
## Methoden in Vtable\-Reihenfolge  
  
|Methode|Description|  
|-------------|-----------------|  
|[IActiveScriptSiteWindow::GetWindow](../../winscript/reference/iactivescriptsitewindow-getwindow.md)|Ruft das Fensterhandle ab, das als der Besitzer eines Popupfensters auftreten kann, das das Skriptmodul anzeigen muss.|  
|[IActiveScriptSiteWindow::EnableModeless](../../winscript/reference/iactivescriptsitewindow-enablemodeless.md)|Veranlasst den Host, sein Hauptfenster sowie alle nicht modale Dialogfelder zu aktivieren oder zu deaktivieren.|  
  
## Siehe auch  
 [Active Script\-Schnittstellen](../../winscript/reference/active-script-interfaces.md)