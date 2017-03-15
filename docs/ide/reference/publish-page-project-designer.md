---
title: "Seite &quot;Ver&#246;ffentlichen&quot;, Projekt-Designer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Projekt-Designer, Seite „Veröffentlichen“"
  - "Seite „Veröffentlichen“ im Projekt-Designer"
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Seite &quot;Ver&#246;ffentlichen&quot;, Projekt-Designer
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die Seite **Veröffentlichen** des **Projekt\-Designers** wird zur Konfiguration von Eigenschaften für die ClickOnce\-Bereitstellung verwendet.  
  
 Wählen Sie zum Aufrufen der Seite **Veröffentlichen** im **Projektmappenexplorer** einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt\-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen**.  
  
> [!NOTE]
>  Einige der hier beschriebenen ClickOnce\-Eigenschaften können auch im **Veröffentlichungs**\-**Assistenten** festgelegt werden, der im Menü **Erstellen** verfügbar ist, oder durch Klicken auf die Schaltfläche**Veröffentlichungs**\-**Assistent** auf dieser Seite.  
  
## UIElement-Liste  
 **Pfad des Veröffentlichungsordners**  
 Gibt den Speicherort an, in dem die Anwendung veröffentlicht wird. Dies kann ein Pfad zum Laufwerk \(`C:\deploy\myapplication`\), eine Dateifreigabe \(`\\server\myapplication`\), ein FTP\-Server \(`ftp://ftp.microsoft.com/myapplication`\) oder eine Website \(`http://www.microsoft.com/myapplication`\) sein. Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen \(**...**\) funktioniert.  
  
 Wenn IIS installiert ist, wird `http://localhost/<projectname>/` als Standardspeicherort verwendet. Wenn IIS nicht installiert ist, wird das Verzeichnis `publish\` verwendet. Wenn auf Ihrem Computer Windows Vista ausgeführt wird, ist der Standardspeicherort immer das Verzeichnis `publish\`, egal, ob Sie IIS installiert haben oder nicht.  
  
 **URL des Installationsordners**  
 Optional. Gibt eine Website an, auf die der Benutzer zugreift, um die Anwendung zu installieren. Dies ist nur erforderlich, wenn sie sich vom **Veröffentlichungsort** unterscheidet, wenn z.B. die Anwendung auf einem Stagingserver veröffentlicht wird.  
  
 **Installationsmodus und \-einstellungen**  
 Bestimmt, ob die Anwendung direkt auf dem **Veröffentlichungsort** ausgeführt wird \(wenn **Anwendung ist nur online verfügbar** ausgewählt ist\) oder installiert und auf dem Menü **Start** sowie dem Untermenü **Programme hinzufügen oder entfernen** der **Systemsteuerung** hinzugefügt wird \(wenn **Die Anwendung ist auch offline verfügbar** ausgewählt ist\).  
  
 Für WPF\-Webbrowseranwendungen ist die Option **Anwendung ist auch offline verfügbar** deaktiviert, da Anwendungen dieser Art nur online verfügbar sind.  
  
 **Anwendungsdateien**  
 Öffnet das [Application Files Dialog Box](http://msdn.microsoft.com/de-de/b06dff3a-b87a-4caf-996b-7a4acf8137a8), das verwendet wird, um anzugeben, wie und wo einzelne Dateien installiert werden  
  
 **Erforderliche Komponenten**  
 Öffnet das [Dialogfeld "Erforderliche Komponenten"](../../ide/reference/prerequisites-dialog-box.md), das verwendet wird, um erforderliche Komponenten wie das .NET Framework anzugeben, das zusammen mit dieser Anwendung installiert wird  
  
 **Updates**  
 Öffnet das [Application Updates Dialog Box](http://msdn.microsoft.com/de-de/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), das verwendet wird, um das Updateverhalten für die Anwendung anzugeben. Dieses Element ist nicht verfügbar, wenn **Anwendung ist nur online verfügbar** ausgewählt ist.  
  
 **Optionen**  
 Öffnet das [Publish Options Dialog Box](http://msdn.microsoft.com/de-de/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), das verwendet wird, um zusätzliche erweiterte Veröffentlichungsoptionen anzugeben  
  
 **Veröffentlichungsversion**  
 Legt die Veröffentlichungsversionsnummer für die Anwendung fest. Wird die Versionsnummer geändert, wird die Anwendung als Update veröffentlicht. Jeder Teil der Veröffentlichungsversion \(**Major**, **Minor**, **Build**, **Revision**\) kann über einen maximalen Wert von 65355 \(<xref:System.UInt16.MaxValue>\) verfügen, das Maximum, das von <xref:System.Version> zugelassen wird.  
  
 Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
 **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen**  
 Optional. Wenn diese Option ausgewählt ist \(Standardeinstellung\), wird der Teil **Revision** der Veröffentlichungsversionsnummer bei jeder Veröffentlichung der Anwendung um eins erhöht. Dies bewirkt, dass die Anwendung als Update veröffentlicht wird.  
  
 **Webpublishing\-Assistent**  
 Öffnet den [Publish Wizard](http://msdn.microsoft.com/de-de/fc6abebd-13d6-48e4-a567-fbc52dad0872). Die Fertigstellung des Veröffentlichungs\-Assistenten hat dieselbe Wirkung wie das Ausführen des Befehls **Veröffentlichen** im Menü **Erstellen**.  
  
 **Jetzt veröffentlichen**  
 Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertig stellen** im **Veröffentlichungs**\-**Assistent**.  
  
## Siehe auch  
 [Publishing ClickOnce Applications](../../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [How to: Specify Where Visual Studio Copies the Files](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [How to: Specify the Location Where End Users Will Install From](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [How to: Specify a Link for Technical Support](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [How to: Specify the ClickOnce Offline or Online Install Mode](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [How to: Enable AutoStart for CD Installations](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [How to: Set the ClickOnce Publish Version](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [How to: Automatically Increment the ClickOnce Publish Version](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [How to: Specify Which Files Are Published by ClickOnce](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [How to: Manage Updates for a ClickOnce Application](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [How to: Change the Publish Language for a ClickOnce Application](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [How to: Specify a Start Menu Name for a ClickOnce Application](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [ClickOnce Security and Deployment](../../deployment/clickonce-security-and-deployment.md)