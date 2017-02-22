---
title: "Publishing ClickOnce Applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.Options"
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.PublishWizard.Help"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "ClickOnce deployment, publishing"
  - "ClickOnce applications, publishing"
  - "applications [Visual Studio], ClickOnce deployment"
  - "deploying applications [ClickOnce], publishing ClickOnce applications"
ms.assetid: eb6dfe79-f54c-4331-8e36-073688e70973
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Publishing ClickOnce Applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim ersten Veröffentlichen einer [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Anwendung können Sie die Veröffentlichungseigenschaften mit dem Webpublishing\-Assistenten festlegen.  Im Assistenten stehen nur wenige Eigenschaften zur Verfügung. Alle anderen Eigenschaften sind auf die Standardwerte eingestellt.  
  
 Spätere Änderungen für die Veröffentlichung der Eigenschaften können im **Projekt\-Designer** auf der Seite **Veröffentlichen** vorgenommen werden.  
  
## Webpublishing\-Assistent  
 Sie können den Webpublishing\-Assistenten verwenden, um die grundlegenden Einstellungen zum Veröffentlichen der Anwendung festzulegen.  Dies sind zum Beispiel die folgenden Veröffentlichungseigenschaften:  
  
-   Speicherort des Veröffentlichungsordners – In diesen Ordner kopiert Visual Studio die Dateien \(lokaler Computer, Netzwerkdateifreigabe, FTP\-Server oder Website\)  
  
-   Speicherort des Installationsordners – Aus diesem Ordner führen Endbenutzer die Installation durch \(Netzwerkdateifreigabe, FTP\-Server, Website, CD\/DVD\)  
  
-   Online\- oder Offlineverfügbarkeit – Ob Endbenutzer mit oder ohne Netzwerkverbindung auf die Anwendung zugreifen können  
  
-   Aktualisierungsrate – Wie häufig die Anwendung eine Prüfung auf neue Updates durchführt  
  
 Weitere Informationen finden Sie unter [How to: Publish a ClickOnce Application using the Publish Wizard](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md).  
  
## Seite "Veröffentlichen"  
 Die Seite **Veröffentlichen** des **Projekt\-Designers** wird zur Konfiguration von Eigenschaften für die ClickOnce\-Bereitstellung verwendet.  In der folgenden Tabelle sind Themen aufgeführt.  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[How to: Specify Where Visual Studio Copies the Files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)|Beschreibt, wie Sie festlegen, wo Visual Studio die Anwendungsdateien und \-manifeste ablegt.|  
|[How to: Specify the Location Where End Users Will Install From](../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)|Beschreibt, wie Sie den Speicherort festlegen, auf den Benutzer zugreifen, um die Anwendung herunterzuladen und zu installieren.|  
|[How to: Specify the ClickOnce Offline or Online Install Mode](../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)|Beschreibt, wie Sie festlegen, ob die Anwendung offline oder online verfügbar sein soll.|  
|[How to: Set the ClickOnce Publish Version](../deployment/how-to-set-the-clickonce-publish-version.md)|Beschreibt, wie Sie die **Publish Version**\-ClickOnce\-Eigenschaft festlegen, die bestimmt, ob die veröffentlichte Anwendung als Update behandelt wird.|  
|[How to: Automatically Increment the ClickOnce Publish Version](../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)|Beschreibt, wie Sie erreichen, dass die Revisionsnummer von **Publish Version** jedes Mal automatisch inkrementiert wird, wenn Sie die Anwendung veröffentlichen.|  
  
 Weitere Informationen finden Sie unter [Seite "Veröffentlichen", Projekt\-Designer](../ide/reference/publish-page-project-designer.md)  
  
### Dialogfeld "Anwendungsdateien"  
 In diesem Dialogfeld können Sie angeben, wie die Dateien im Projekt zur Veröffentlichung, Aktualisierung und zum dynamischen Download kategorisiert werden.  Es enthält ein Raster der Projektdateien, die standardmäßig nicht ausgeschlossen sind bzw. die über eine Downloadgruppe verfügen.  
  
 Informationen zum Ausschließen von Dateien, Kennzeichnen von Dateien als Datendateien oder erforderliche Komponenten und Erstellen von Dateigruppen zur bedingten Installation auf der Visual Studio\-Benutzeroberfläche finden Sie unter [How to: Specify Which Files Are Published by ClickOnce](../deployment/how-to-specify-which-files-are-published-by-clickonce.md).  Sie können Datendateien auch mit Mage.exe kennzeichnen.  Weitere Informationen finden Sie unter [How to: Include a Data File in a ClickOnce Application](../deployment/how-to-include-a-data-file-in-a-clickonce-application.md).  
  
### Dialogfeld "Erforderliche Komponenten"  
 In diesem Dialogfeld wird festgelegt, welche erforderlichen Komponenten installiert werden und wie die Installation ausgeführt wird.  Weitere Informationen finden Sie unter [How to: Install Prerequisites with a ClickOnce Application](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) und [Dialogfeld "Erforderliche Komponenten"](../ide/reference/prerequisites-dialog-box.md).  
  
### Dialogfeld "Anwendungsupdates"  
 In diesem Dialogfeld wird angegeben, wie bei der Anwendungsinstallation nach Updates gesucht werden soll.  Weitere Informationen finden Sie unter [How to: Manage Updates for a ClickOnce Application](../deployment/how-to-manage-updates-for-a-clickonce-application.md).  
  
### Dialogfeld "Veröffentlichungsoptionen"  
 Im Dialogfeld Veröffentlichungsoptionen werden die Bereitstellungsoptionen einer Anwendung angegeben.  
  
|||  
|-|-|  
|[How to: Change the Publish Language for a ClickOnce Application](../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)|Beschreibt, wie Sie eine Sprache und eine Kultur angeben, die mit der lokalisierten Version übereinstimmen.|  
|[How to: Specify a Start Menu Name for a ClickOnce Application](../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)|Beschreibt, wie Sie den Anzeigenamen für eine ClickOnce\-Anwendung ändern.|  
|[How to: Specify a Link for Technical Support](../deployment/how-to-specify-a-link-for-technical-support.md)|Beschreibt, wie Sie die **Support URL**\-Eigenschaft festlegen, die eine Webseite oder Dateifreigabe angibt, von der Benutzer Informationen zur Anwendung abrufen können.|  
|[How to: Specify a Support URL for Individual Prerequisites in a ClickOnce Deployment](../deployment/how-to-specify-a-support-url-for-individual-prerequisites-in-a-clickonce-deployment.md)|Veranschaulicht, wie ein Anwendungsmanifest manuell geändert wird, um für die jeweilige erforderliche Komponente einzelne Support\-URLs aufzunehmen.|  
|[How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)|Beschreibt, wie Sie zusammen mit der Anwendung eine Standardwebseite \(publish.htm\) generieren und veröffentlichen.|  
|[Gewusst wie: Anpassen der ClickOnce\-Standardwebseite](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)|Beschreibt, wie Sie die Webseite anpassen, die zusammen mit der Anwendung automatisch generiert und veröffentlicht wird.|  
|[How to: Enable AutoStart for CD Installations](../deployment/how-to-enable-autostart-for-cd-installations.md)|Beschreibt, wie Sie AutoStart aktivieren, damit die ClickOnce\-Anwendung beim Einlegen des Datenträgers automatisch gestartet wird.|  
  
## Verwandte Themen  
  
|Titel|Beschreibung|  
|-----------|------------------|  
|[How to: Create File Associations For a ClickOnce Application](../deployment/how-to-create-file-associations-for-a-clickonce-application.md)|Beschreibt, wie Sie einer ClickOnce\-Anwendung die Unterstützung für Dateinamenerweiterungen hinzufügen.|  
|[Gewusst wie: Abrufen von Abfragezeichenfolgen\-Informationen in einer Online\-ClickOnce\-Anwendung](../deployment/how-to-retrieve-query-string-information-in-an-online-clickonce-application.md)|Veranschaulicht, wie die Parameter aus der URL abgerufen werden, mit denen eine ClickOnce\-Anwendung ausgeführt wird.|  
|[How to: Disable URL Activation of ClickOnce Applications by Using the Designer](../deployment/how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer.md)|Beschreibt, wie Sie mit dem Designer vorgeben können, dass Benutzer die Anwendung über das Menü **Start** starten müssen.|  
|[How to: Disable URL Activation of ClickOnce Applications](../deployment/how-to-disable-url-activation-of-clickonce-applications.md)|Beschreibt, wie Sie vorgeben können, dass Benutzer die Anwendung über das Menü **Start** starten müssen.|  
|[Exemplarische Vorgehensweise: Bedarfsgerechtes Herunterladen von Assemblys mit der API für die ClickOnce\-Bereitstellung unter Verwendung des Designers](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer.md)|Erklärt, wie Anwendungsassemblys erst bei der ersten Verwendung durch die Anwendung mit dem Designer heruntergeladen werden.|  
|[Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API](../deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Erklärt, wie Anwendungsassemblys erst bei der ersten Verwendung durch die Anwendung heruntergeladen werden.|  
|[Walkthrough: Downloading Satellite Assemblies on Demand with the ClickOnce Deployment API](../deployment/walkthrough-downloading-satellite-assemblies-on-demand-with-the-clickonce-deployment-api.md)|Beschreibt, wie Sie Ihre Satellitenassemblys als optional kennzeichnen und nur die Assembly herunterladen, die ein Clientcomputer für die eigenen aktuellen Kultureinstellungen benötigt.|  
|[Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)|Erklärt, wie .NET Framework\-Dienstprogramme verwendet werden, um ClickOnce\-Anwendungen bereitzustellen.|  
|[Walkthrough: Manually Deploying a ClickOnce Application that Does Not Require Re\-Signing and that Preserves Branding Information](../deployment/walkthrough-manually-deploying-a-clickonce-application-that-does-not-require-re-signing-and-that-preserves-branding-information.md)|Erklärt, wie .NET Framework\-Hilfsprogramme verwendet werden, um die ClickOnce\-Anwendung bereitzustellen, ohne die Manifeste neu zu signieren.|  
|[NIB: How to: Optimize an Application for a Specific CPU Type](http://msdn.microsoft.com/de-de/294a75d2-4279-4b72-8298-2bea05be907a)|Erklärt, wie Sie die Veröffentlichung für einen 64\-Bit\-Prozessor durchführen, indem Sie im Projekt die **Target CPU**\- oder **Platform target**\-Eigenschaft ändern.|  
|[Walkthrough: Enabling a ClickOnce Application to Run on Multiple .NET Framework Versions](http://msdn.microsoft.com/de-de/7f4383af-ed87-4853-b4d4-02a3967a5fd9)|Erklärt, wie Sie eine ClickOnce\-Anwendung so aktivieren, dass sie auf mehreren Versionen von .NET Framework installiert und ausgeführt wird.|  
|[Walkthrough: Creating a Custom Installer for a ClickOnce Application](../deployment/walkthrough-creating-a-custom-installer-for-a-clickonce-application.md)|Erklärt, wie Sie ein benutzerdefiniertes Installationsprogramm erstellen, um eine ClickOnce\-Anwendung zu installieren.|  
|[How to: Publish a WPF Application with Visual Styles Enabled](../deployment/how-to-publish-a-wpf-application-with-visual-styles-enabled.md)|Stellt detaillierte Anweisungen zum Auflösen eines Fehlers bereit, der angezeigt wird, wenn Sie versuchen, eine WPF\-Anwendung zu veröffentlichen, bei der visuelle Stile aktiviert sind.|  
  
## Siehe auch  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [ClickOnce Reference](../deployment/clickonce-reference.md)