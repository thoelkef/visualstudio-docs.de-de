---
title: "How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API | Microsoft Docs"
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
  - "ClickOnce deployment, updates"
  - "application updates"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ClickOnce bietet zwei Möglichkeiten, eine bereitgestellte Anwendung zu aktualisieren.  Mit der ersten Methode können Sie die ClickOnce\-Bereitstellung so konfigurieren, dass in bestimmten Intervallen automatisch nach Updates gesucht wird.  Mit der zweiten Methode können Sie Code schreiben, der mit der <xref:System.Deployment.Application.ApplicationDeployment>\-Klasse auf der Grundlage eines Ereignisses, z. B. einer Benutzeranforderung, nach Updates sucht.  
  
 In den folgenden Verfahren wird Code für ein programmgesteuertes Update gezeigt und beschrieben, wie die ClickOnce\-Bereitstellung für die Aktivierung der programmgesteuerten Suche nach Updates konfiguriert wird.  
  
 Sie müssen einen Speicherort für Updates angeben, damit eine ClickOnce\-Anwendung programmgesteuert aktualisiert werden kann.  Dies wird auch als Bereitstellungsanbieter bezeichnet.  Weitere Informationen zur Einstellung dieser Eigenschaft finden Sie unter [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  Sie können die im Folgenden beschriebene Methode auch einsetzen, um Ihre Anwendungen von einem Ort aus bereitzustellen, sie aber von einem anderen Ort aus zu aktualisieren.  Weitere Informationen finden Sie unter [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### So werden Updates programmgesteuert gesucht  
  
1.  Erstellen Sie mit den von Ihnen bevorzugten Befehlszeilen\- oder visuellen Tools eine neue Windows Forms\-Anwendung.  
  
2.  Erstellen Sie eine beliebige Schaltfläche, ein Menüelement oder ein anderes Benutzeroberflächenelement, das Benutzer für die Suche nach Updates auswählen sollen.  Rufen Sie vom Ereignishandler dieses Elements die folgende Methode auf, um nach Updates zu suchen und sie zu installieren.  
  
     [!code-cs[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]  
  
3.  Kompilieren Sie Ihre Anwendung.  
  
### Verwenden von Mage.exe, um eine Anwendung bereitzustellen, die programmgesteuert nach Updates sucht  
  
-   Befolgen Sie die Anweisungen zum Bereitstellen der Anwendung mit Mage.exe, wie in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) erläutert.  Wenn Sie Mage.exe aufrufen, um das Bereitstellungsmanifest zu generieren, achten Sie darauf, dass Sie den `providerUrl`\-Befehlszeilenschalter verwenden und die URL angeben, unter der ClickOnce nach Updates suchen soll.  Wenn Ihre Anwendung z. B. von [http:\/\/www.microsoft.com\/de\/de\/default.aspx](http://www.microsoft.com/de/de/default.aspx) aus aktualisiert, könnte Ihr Aufruf für die Generierung des Bereitstellungsmanifests folgendermaßen aussehen:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### Verwenden von MageUI.exe, um eine Anwendung bereitzustellen, die programmgesteuert nach Updates sucht  
  
-   Befolgen Sie die Anweisungen zum Bereitstellen der Anwendung mit Mage.exe, wie in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md) erläutert.  Legen Sie auf der Registerkarte **Bereitstellungsoptionen** für das Feld **Startspeicherort** das Anwendungsmanifest fest, in dem ClickOnce nach Updates suchen soll.  Deaktivieren Sie auf der Registerkarte **Aktualisierungsoptionen** das Kontrollkästchen **Die Anwendung soll nach Updates suchen**.  
  
## .NET Framework-Sicherheit  
 Die Anwendung muss Berechtigungen für volle Vertrauenswürdigkeit haben, um die programmgesteuerte Aktualisierung zu verwenden.  
  
## Siehe auch  
 [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)