---
title: "Vorbereitung zum Debuggen: ASP.NET-Webanwendungen | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Debuggen [Visual Studio], Webanwendungen"
  - "Debuggen von ASP.NET-Webanwendungen"
ms.assetid: bcfb1080-98d1-42f9-96af-186fb14f232a
caps.latest.revision: 35
caps.handback.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Vorbereitung zum Debuggen: ASP.NET-Webanwendungen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Websitevorlage erstellt eine Web Form\-Anwendung.  Wenn Sie mit dieser Vorlage eine Website erstellen, legt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die Standardeinstellungen für das Debuggen fest.  Im Dialogfeld **Projekteigenschaften** können Sie angeben, ob Sie die Webseite als Startseite einrichten möchten.  Wenn Sie das Debuggen einer [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Website mit diesen Standardeinstellungen beginnen, startet [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Internet Explorer und fügt den Debugger an den [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-Arbeitsprozess \(aspnet\_wp.exe oder w3wp.exe\) an.  Weitere Informationen finden Sie unter [Systemanforderungen](../debugger/aspnet-debugging-system-requirements.md).  
  
### So erstellen Sie eine Web Forms\-Anwendung  
  
1.  Wählen Sie im Menü **Datei Neue Website** aus.  
  
2.  Wählen Sie im Dialogfeld **Neue Website** die Option [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)]\-**Website** aus.  
  
3.  Klicken Sie auf **OK**.  
  
### So debuggen Sie Web Forms  
  
1.  Legen Sie in den Funktionen und Ereignishandlern einen oder mehrere Haltepunkte fest.  
  
     Weitere Informationen finden Sie unter [Breakpoints and Tracepoints](http://msdn.microsoft.com/de-de/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
2.  Wenn ein Haltepunkt erreicht wird, wird der Code in der Funktion schrittweise durchlaufen.  Achten Sie auf die Ausführung des Codes, bis Sie das Problem isolieren.  
  
     Weitere Informationen finden Sie unter [Stepping](http://msdn.microsoft.com/de-de/8791dac9-64d1-4bb9-b59e-8d59af1833f9) und unter [Debuggen von Webanwendungen und Skripts](../debugger/debugging-web-applications-and-script.md).  
  
## Ändern von Standardkonfigurationen  
 Bei Bedarf können Sie die von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellten standardmäßigen Debug\- und Releasekonfigurationen ändern.  Weitere Informationen hierzu finden Sie unter [Gewusst wie: Festlegen von Debug\- und Releasekonfigurationen](../debugger/how-to-set-debug-and-release-configurations.md).  
  
#### So ändern Sie die Standarddebugkonfiguration  
  
1.  Klicken Sie im **Projektmappen\-Explorer** mit der rechten Maustaste auf die Website, und wählen Sie **Eigenschaftenseiten** aus, um das Dialogfeld **Eigenschaftenseiten** zu öffnen.  
  
2.  Klicken Sie auf **Startoptionen**.  
  
3.  Legen Sie für **Startaktion** die Webseite fest, die zuerst angezeigt werden soll.  
  
4.  Stellen Sie sicher, dass unter **Debugger** die Option **ASP.NET\-Debuggen** ausgewählt ist.  
  
     Weitere Informationen finden Sie unter [Einstellungen von Eigenschaftenseiten für Webprojekte](../debugger/property-pages-settings-for-web-projects.md).  
  
## Siehe auch  
 [Einstellungen und Vorbereitung für das Debuggen](../debugger/debugger-settings-and-preparation.md)   
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)