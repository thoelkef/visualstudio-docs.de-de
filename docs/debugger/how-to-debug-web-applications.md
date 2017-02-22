---
title: "Gewusst wie: Debuggen von Webanwendungen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ASP.NET-Web Forms, Debuggen"
  - "ASP.NET, Debuggen von Webanwendungen"
  - "Debuggen von ASP.NET-Webanwendungen, Während der Entwicklung"
  - "Webdienste, Debuggen"
ms.assetid: 6440d12e-6b29-42c5-a958-99aeaaff480f
caps.latest.revision: 37
caps.handback.revision: 37
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Gewusst wie: Debuggen von Webanwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] ist die Haupttechnologie für die Entwicklung von Webanwendungen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  Der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Debugger bietet Ihnen leistungsfähige Tools zum Debuggen von [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendungen, die lokal oder auf einem Remoteserver ausgeführt werden.  In diesem Thema wird beschrieben, wie ein [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Projekt während der Entwicklung gedebuggt wird.  Weitere Informationen zum Debuggen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Webanwendung, die bereits auf einem Produktionsserver bereitgestellt wird, finden Sie unter [Debuggen bereitgestellter Webanwendungen](../debugger/debugging-deployed-web-applications.md).  
  
 So debuggen Sie eine [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Anwendung  
  
-   Sie müssen über die erforderlichen Berechtigungen verfügen.  Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
-   Das [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Debuggen muss in den **Projekteigenschaften** aktiviert werden.  
  
-   In der Konfigurationsdatei der Anwendung \(Web.config\) muss der Debugmodus festgelegt sein.  Der Debugmodus veranlasst [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)] zum Erstellen von Symbolen für dynamisch generierte Dateien und ermöglicht dem Debugger das Hinzufügen zur Anwendung [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] legt dies beim Starten des Debugvorgangs automatisch fest, wenn Sie das Projekt aus der Webprojekte\-Vorlage erstellt haben.  
  
-   Weitere Informationen finden Sie unter [Gewusst wie: Debuggen für ASP.NET\-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md).  
  
### So debuggen Sie Webanwendungen während der Entwicklung  
  
1.  Klicken Sie im Menü **Debuggen** auf **Starten**, um das Debuggen der Webanwendung zu starten.  
  
     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt das Webanwendungsprojekt, stellt ggf. die Anwendung bereit, startet den ASP.NET Development Server, wenn Sie lokal debuggen, und fügt sie an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess an.  
  
2.  Verwenden Sie den Debugger, um Haltepunkte festzulegen bzw. zu entfernen, schrittweise auszuführen und andere Debugoperationen auszuführen. Gehen Sie dabei genauso wie bei allen anderen Anwendungen vor.  
  
     Weitere Informationen finden Sie unter [Debugger – Grundlagen](../debugger/debugger-basics.md).  
  
3.  Klicken Sie im Menü **Debuggen** auf **Debuggen beenden**, um die Debugsitzung abzuschließen, oder klicken Sie in Internet Explorer im Menü **Datei** auf **Schließen**.  
  
## Siehe auch  
 [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md)   
 [Debuggen von ASP.NET\- und AJAX\-Anwendungen](../debugger/debugging-aspnet-and-ajax-applications.md)   
 [Gewusst wie: Debuggen für ASP.NET\-Anwendungen aktivieren](../debugger/how-to-enable-debugging-for-aspnet-applications.md)