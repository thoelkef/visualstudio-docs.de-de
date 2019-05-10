---
title: Seite „Veröffentlichen“, Projekt-Designer | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- Microsoft.VisualStudio.Publish.ClickOnceProvider.Dialog.PropertyPage
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Project Designer, Publish page
- Publish page in Project Designer
ms.assetid: 153527c6-8b95-4003-8e8e-03a489d0a629
caps.latest.revision: 37
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f50c5897f68e43071d4920f85f1a694cacbf655
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441311"
---
# <a name="publish-page-project-designer"></a>Seite "Veröffentlichen", Projekt-Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die ClickOnce-Bereitstellung verwendet.  
  
 Wählen Sie zum Aufrufen der Seite **Veröffentlichen** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** .  
  
> [!NOTE]
> Einige der hier beschriebenen ClickOnce-Eigenschaften können auch im **Veröffentlichungs-Assistent** festgelegt werden, der im Menü **Erstellen** verfügbar ist, oder durch Klicken auf die Schaltfläche**Veröffentlichungs-Assistent** auf dieser Seite.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **Pfad des Veröffentlichungsordners**  
 Gibt den Speicherort an, in dem die Anwendung veröffentlicht wird. Dies kann ein Pfad zum Laufwerk (`C:\deploy\myapplication`), eine Dateifreigabe (`\\server\myapplication`), ein FTP-Server (`ftp://ftp.microsoft.com/myapplication`) oder eine Website (`http://www.microsoft.com/myapplication`) sein. Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen (**...**) funktioniert.  
  
 Wenn IIS installiert ist, wird `http://localhost/<projectname>/` als Standardspeicherort verwendet. Wenn IIS nicht installiert ist, wird das Verzeichnis `publish\` verwendet. Wenn auf Ihrem Computer Windows Vista ausgeführt wird, ist der Standardspeicherort immer das Verzeichnis `publish\` , egal, ob Sie IIS installiert haben oder nicht.  
  
 **URL des Installationsordners**  
 Dies ist optional. Gibt eine Website an, auf die der Benutzer zugreift, um die Anwendung zu installieren. Dies ist nur erforderlich, wenn sie sich vom **Veröffentlichungsort**unterscheidet, wenn z.B. die Anwendung auf einem Stagingserver veröffentlicht wird.  
  
 **Installationsmodus und -einstellungen**  
 Bestimmt, ob die Anwendung direkt auf dem **Veröffentlichungsort** ausgeführt wird (wenn **Anwendung ist nur online verfügbar** ausgewählt ist) oder installiert und auf dem Menü **Start** sowie dem Untermenü **Programme hinzufügen oder entfernen** der **Systemsteuerung** hinzugefügt wird (wenn **Die Anwendung ist auch offline verfügbar** ausgewählt ist).  
  
 Für WPF-Webbrowseranwendungen ist die Option **Anwendung ist auch offline verfügbar** deaktiviert, da Anwendungen dieser Art nur online verfügbar sind.  
  
 **Anwendungsdateien**  
 Öffnet das Dialogfeld [Anwendungsdateien](http://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), mit dem angegeben wird, wie und wo einzelne Dateien installiert sind  
  
 **Erforderliche Komponenten**  
 Öffnet das [Dialogfeld „Erforderliche Komponenten“](../../ide/reference/prerequisites-dialog-box.md), mit dem erforderliche Komponenten wie das .NET Framework angegeben werden, die zusammen mit dieser Anwendung installiert werden  
  
 **Updates**  
 Öffnet das [Dialogfeld „Anwendungsupdates“](http://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), mit dem das Updateverhalten der Anwendung angegeben wird. Dieses Element ist nicht verfügbar, wenn **Anwendung ist nur online verfügbar** ausgewählt ist.  
  
 **Optionen**  
 Öffnet das [Dialogfeld „Veröffentlichungsoptionen“](http://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), mit dem zusätzliche erweiterte Veröffentlichungsoptionen angegeben werden  
  
 **Veröffentlichungsversion**  
 Legt die Veröffentlichungsversionsnummer für die Anwendung fest. Wird die Versionsnummer geändert, wird die Anwendung als Update veröffentlicht. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann den Maximalwert 65355 (<xref:System.UInt16.MaxValue>) haben, d.h. das von <xref:System.Version> zugelassene Maximum.  
  
 Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.  
  
 **Revisionsnummer automatisch mit jeder Veröffentlichung erhöhen**  
 Dies ist optional. Wenn diese Option ausgewählt ist (Standardeinstellung), wird der Teil **Revision** der Veröffentlichungsversionsnummer bei jeder Veröffentlichung der Anwendung um eins erhöht. Dies bewirkt, dass die Anwendung als Update veröffentlicht wird.  
  
 **Veröffentlichungs-Assistent**  
 Öffnet den [Veröffentlichungs-Assistenten](http://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Die Fertigstellung des Veröffentlichungs-Assistenten hat dieselbe Wirkung wie das Ausführen des Befehls **Veröffentlichen** im Menü **Erstellen** .  
  
 **Jetzt veröffentlichen**  
 Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertigstellen** im **Veröffentlichungs-Assistenten**.  
  
## <a name="see-also"></a>Siehe auch  
 [Veröffentlichen von ClickOnce-Anwendungen](../../deployment/publishing-clickonce-applications.md)   
 [Vorgehensweise: Veröffentlichen einer ClickOnce-Anwendung, die mit dem Webpublishing-Assistenten](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)   
 [Vorgehensweise: Geben Sie, in denen Visual Studio die Dateien kopiert an](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Vorgehensweise: Geben Sie den Speicherort, in dem von Endbenutzern installieren](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md)   
 [Vorgehensweise: Geben Sie einen Link für den technischen Support](../../deployment/how-to-specify-a-link-for-technical-support.md)   
 [Vorgehensweise: Geben Sie die ClickOnce Offline oder Online-Installationsmodus](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md)   
 [Vorgehensweise: Aktivieren von AutoStart für Installationen von CD](../../deployment/how-to-enable-autostart-for-cd-installations.md)   
 [Vorgehensweise: Festlegen der ClickOnce-Veröffentlichungsversion](../../deployment/how-to-set-the-clickonce-publish-version.md)   
 [Vorgehensweise: Automatisches Erhöhen der ClickOnce-Veröffentlichungsversion](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md)   
 [Vorgehensweise: Angeben der mit ClickOnce veröffentlichten Dateien](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md)   
 [Vorgehensweise: Installieren der erforderlichen Komponenten mit einer ClickOnce-Anwendung](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)   
 [Vorgehensweise: Verwalten von Aktualisierungen für eine ClickOnce-Anwendung](../../deployment/how-to-manage-updates-for-a-clickonce-application.md)   
 [Vorgehensweise: Ändern der Veröffentlichungssprache einer ClickOnce-Anwendung](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md)   
 [Vorgehensweise: Angeben eines Namens für eine ClickOnce-Anwendung im Menü](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md)   
 [Vorgehensweise: Angeben einer Veröffentlichungsseite für eine ClickOnce-Anwendung](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)   
 [ClickOnce-Sicherheit und Bereitstellung](../../deployment/clickonce-security-and-deployment.md)
