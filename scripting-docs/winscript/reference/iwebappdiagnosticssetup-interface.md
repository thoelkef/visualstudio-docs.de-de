---
title: "IWebAppDiagnosticsSetup-Schnittstelle | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "IWebAppDiagnosticsSetup-Schnittstelle"
ms.assetid: ec7359f2-633e-4d59-b64b-9cab0134dfd0
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# IWebAppDiagnosticsSetup-Schnittstelle
Diese Schnittstelle wird von einer Debugsitzung Anwendung PDM, COM\-Objekte im Prozess erstellt, der gedebuggt wird und Internet\-Diagnose zu aktivieren implementiert.  Wenn die PDM Anwendungsobjektwerkzeuge, [IObjectWithSite](http://go.microsoft.com/fwlink/?LinkId=232438) Internet Explorer\-Aufrufe [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) dafür debuggen, nachdem es und übergibt in einem Verweis auf [IWebBrowser2](http://go.microsoft.com/fwlink/?LinkId=232449) erstellt wurde.  ruft [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) und übergibt einer WWA\-Anwendung im WWA schließen IWebApplicationHost stattdessen an.  Wenn [SetSite](http://go.microsoft.com/fwlink/?LinkId=232439) mit einem Wert ungleich null angibt aufgerufen wurde, [IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md) true zurück.  Wenn nicht, gibt er false zurück und ruft auf [IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md) schlagen fehl.  
  
> [!IMPORTANT]
>  `IWebAppDiagnosticsSetup` wird durch PDM v11.0 und höher implementiert.  Fundumgebung activdbg100.h.  
  
## Methoden  
 Diese Schnittstelle macht die folgenden Methoden verfügbar.  
  
|Methode|Description|  
|-------------|-----------------|  
|[IWebAppDiagnosticsSetup::CreateObjectWithSiteAtWebApp](../../winscript/reference/iwebappdiagnosticssetup-createobjectwithsiteatwebapp.md)|Ruft die Textdokumente ab, die von den angegebenen Filter ausgeblendet werden.|  
|[IWebAppDiagnosticsSetup::DiagnosticsSupported](../../winscript/reference/iwebappdiagnosticssetup-diagnosticssupported.md)|Bestimmt, ob das angegebene Dokument auf einen der untergeordneten Knoten des Knotens gehört.|