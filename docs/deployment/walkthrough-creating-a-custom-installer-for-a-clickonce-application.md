---
title: "Walkthrough: Creating a Custom Installer for a ClickOnce Application | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, custom installer"
  - "installer [ClickOnce], custom"
  - "deploying applications [ClickOnce], custom installer"
  - "InPlaceHostingManager [ClickOnce], custom installer"
  - "custom installer [ClickOnce]"
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
caps.latest.revision: 34
caps.handback.revision: 34
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Walkthrough: Creating a Custom Installer for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Jede ClickOnce\-Anwendung, die auf einer EXE\-Datei basiert, kann von einem benutzerdefinierten Installer automatisch installiert und aktualisiert werden.  Ein benutzerdefinierter Installer kann während der Installation benutzerdefinierte Optionen implementieren, einschließlich benutzerdefinierter Dialogfelder für Sicherheits\- und Wartungsvorgänge.  Der benutzerdefinierte Installer führt Installationsvorgänge mithilfe der <xref:System.Deployment.Application.InPlaceHostingManager>\-Klasse aus.  Diese exemplarische Vorgehensweise veranschaulicht, wie ein benutzerdefinierter Installer erstellt wird, der automatisch eine ClickOnce\-Anwendung installiert.  
  
## Vorbereitungsmaßnahmen  
  
### So erstellen Sie einen benutzerdefinierten Installer für eine ClickOnce\-Anwendung  
  
1.  Fügen Sie in der ClickOnce\-Anwendung Verweise auf "System.Deployment" und "System.Windows.Forms" hinzu.  
  
2.  Fügen Sie der Anwendung eine neue Klasse hinzu, und geben Sie einen beliebigen Namen an.  In dieser exemplarischen Vorgehensweise wird der Name `MyInstaller` verwendet.  
  
3.  Fügen Sie am Anfang der neuen Klasse die Anweisung `Imports` oder `using` hinzu.  
  
    ```vb#  
    Imports System.Deployment.Application  
    Imports System.Windows.Forms  
    ```  
  
    ```c#  
    using System.Deployment.Application;  
    using System.Windows.Forms;  
    ```  
  
4.  Fügen Sie der Klasse die folgenden Methoden hinzu.  
  
     Diese Methoden rufen <xref:System.Deployment.Application.InPlaceHostingManager>\-Methoden auf, um das Bereitstellungsmanifest herunterzuladen, entsprechende Berechtigungen zu gewähren, beim Benutzer die Berechtigung zum Installieren anzufordern und dann die Anwendung in den ClickOnce\-Cache herunterzuladen und zu installieren.  Ein benutzerdefinierter Installer kann angeben, dass eine ClickOnce\-Anwendung vorerst vertrauenswürdig ist, oder die Vertrauensentscheidung an den <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>\-Methodenaufruf verweisen.  Dieser Code stuft die Anwendung vorerst als vertrauenswürdig ein.  
  
    > [!NOTE]
    >  Berechtigungen, die durch eine Einstufung als vorerst vertrauenswürdig erteilt werden, können nicht die Berechtigungen überschreiten, die im Code des benutzerdefinierten Installers definiert sind.  
  
     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-cs[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]  
  
5.  Um die Anwendung über den Code zu installieren, rufen Sie die `InstallApplication`\-Methode auf.  Wenn Sie der Klasse z. B. den Namen `MyInstaller` gegeben haben, könnten Sie `InstallApplication` wie folgt aufrufen.  
  
    ```vb#  
    Dim installer As New MyInstaller()  
    installer.InstallApplication("\\myServer\myShare\myApp.application")  
    MessageBox.Show("Installer object created.")  
    ```  
  
    ```c#  
    MyInstaller installer = new MyInstaller();  
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");  
    MessageBox.Show("Installer object created.");  
  
    ```  
  
## Nächste Schritte  
 Eine ClickOnce\-Anwendung kann auch benutzerdefinierte Aktualisierungslogik hinzufügen, einschließlich einer benutzerdefinierten Benutzeroberfläche, die beim Aktualisierungsvorgang angezeigt wird.  Weitere Informationen finden Sie unter <xref:System.Deployment.Application.UpdateCheckInfo>.  Eine ClickOnce\-Anwendung kann auch den standardmäßigen Startmenüeintrag, die Verknüpfung und den Eintrag unter "Software" mithilfe des `<customUX>`\-Elements unterdrücken.  Weitere Informationen finden Sie unter [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md) und <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.  
  
## Siehe auch  
 [ClickOnce Application Manifest](../deployment/clickonce-application-manifest.md)   
 [\<entryPoint\> Element](../deployment/entrypoint-element-clickonce-application.md)