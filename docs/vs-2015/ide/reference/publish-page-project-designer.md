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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 391e6c457dd09afa154c46cbc8644f028052cb32
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665706"
---
# <a name="publish-page-project-designer"></a>Seite "Veröffentlichen", Projekt-Designer
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die Seite **Veröffentlichen** des **Projekt-Designers** wird zur Konfiguration von Eigenschaften für die ClickOnce-Bereitstellung verwendet.

 Wählen Sie zum Aufrufen der Seite **Veröffentlichen** im **Projektmappenexplorer**einen Projektknoten aus, und klicken Sie anschließend im Menü **Projekt** auf **Eigenschaften**. Sobald der **Projekt-Designer** angezeigt wird, klicken Sie auf die Registerkarte **Veröffentlichen** .

> [!NOTE]
> Einige der hier beschriebenen ClickOnce-Eigenschaften können auch im **Veröffentlichungs-Assistent** festgelegt werden, der im Menü **Erstellen** verfügbar ist, oder durch Klicken auf die Schaltfläche**Veröffentlichungs-Assistent** auf dieser Seite.

## <a name="uielement-list"></a>UIElement-Liste
 **Ort des Veröffentlichungs Ordners** Gibt den Speicherort an, an dem die Anwendung veröffentlicht wird. Dies kann ein Pfad zum Laufwerk (`C:\deploy\myapplication`), eine Dateifreigabe (`\\server\myapplication`), ein FTP-Server (`ftp://ftp.microsoft.com/myapplication`) oder eine Website (`http://www.microsoft.com/myapplication`) sein. Beachten Sie, dass im Feld **Ort der Veröffentlichung** Text angegeben sein muss, damit die Schaltfläche zum Durchsuchen ( **...** ) funktioniert.

 Wenn IIS installiert ist, wird `http://localhost/<projectname>/` als Standardspeicherort verwendet. Wenn IIS nicht installiert ist, wird das Verzeichnis `publish\` verwendet. Wenn auf Ihrem Computer Windows Vista ausgeführt wird, ist der Standardspeicherort immer das Verzeichnis `publish\` , egal, ob Sie IIS installiert haben oder nicht.

 **URL des Installations Ordners** Optionale. Gibt eine Website an, auf die der Benutzer zugreift, um die Anwendung zu installieren. Dies ist nur erforderlich, wenn sie sich vom **Veröffentlichungsort**unterscheidet, wenn z.B. die Anwendung auf einem Stagingserver veröffentlicht wird.

 **Installationsmodus und Einstellungen** Bestimmt, ob die Anwendung direkt aus dem **Veröffentlichungsort** ausgeführt wird (wenn **die Anwendung nur online verfügbar** ist ausgewählt ist) oder installiert und dem **Startmenü** **und dem Element** "Software" in hinzugefügt wird. **Systemsteuerung** (wenn **die Anwendung auch offline verfügbar** ist) ausgewählt ist.

 Für WPF-Webbrowseranwendungen ist die Option **Anwendung ist auch offline verfügbar** deaktiviert, da Anwendungen dieser Art nur online verfügbar sind.

 **Anwendungs Dateien** Öffnet das [Dialog Feld Anwendungs Dateien](https://msdn.microsoft.com/b06dff3a-b87a-4caf-996b-7a4acf8137a8), das verwendet wird, um anzugeben, wie und wo einzelne Dateien installiert werden.

 Erforderliche Komponenten Öffnet das [Dialog Feld](../../ide/reference/prerequisites-dialog-box.md)"erforderliche Komponenten", mit dem erforderliche Komponenten wie die .NET Framework angegeben werden, die in Verbindung mit der Anwendung installiert werden sollen.

 **Updates** Öffnet das [Dialog Feld Anwendungs Updates](https://msdn.microsoft.com/8eca8743-8e68-4d04-bfd5-4dc0a9b2934f), das verwendet wird, um das Update Verhalten für die Anwendung anzugeben. Dieses Element ist nicht verfügbar, wenn **Anwendung ist nur online verfügbar** ausgewählt ist.

 **Optionen** Öffnet das [Dialog Feld Veröffentlichungs Optionen](https://msdn.microsoft.com/fd9baa1b-7311-4f9e-8ffb-ae50cf110592), in dem zusätzliche erweiterte Veröffentlichungs Optionen angegeben werden.

 **Veröffentlichungs Version** Legt die Veröffentlichungs Versionsnummer für die Anwendung fest. Wenn die Versionsnummer geändert wird, wird die Anwendung als Update veröffentlicht. Jeder Teil der Veröffentlichungsversion (**Hauptversion**, **Nebenversion**, **Build**, **Revision**) kann den Maximalwert 65355 (<xref:System.UInt16.MaxValue>) haben, d.h. das von <xref:System.Version> zugelassene Maximum.

 Wenn Sie mit ClickOnce mehrere Versionen einer Anwendung installieren, verschiebt die Installation ältere Versionen der Anwendung in einen Ordner mit dem Namen Archiv in dem von Ihnen angegebenen Veröffentlichungsort. Durch dieses Archivieren älterer Versionen wird sichergestellt, dass im Installationsverzeichnis keine Ordner älterer Versionen verbleiben.

 **Revision automatisch mit jeder Veröffentlichung erhöhen** Optionale. Wenn diese Option ausgewählt ist (Standardeinstellung), wird der Teil **Revision** der Veröffentlichungsversionsnummer bei jeder Veröffentlichung der Anwendung um eins erhöht. Dies bewirkt, dass die Anwendung als Update veröffentlicht wird.

 **Webpublishing-Assistent** Öffnet den [Veröffentlichungs-Assistenten](https://msdn.microsoft.com/fc6abebd-13d6-48e4-a567-fbc52dad0872). Die Fertigstellung des Veröffentlichungs-Assistenten hat dieselbe Wirkung wie das Ausführen des Befehls **Veröffentlichen** im Menü **Erstellen** .

 **Jetzt veröffentlichen** Veröffentlicht die Anwendung mithilfe der aktuellen Einstellungen. Entspricht der Schaltfläche **Fertigstellen** im **Veröffentlichungs-Assistenten**.

## <a name="see-also"></a>Siehe auch
 Veröffentlichen von [ClickOnce-Anwendungen](../../deployment/publishing-clickonce-applications.md) Gewusst [wie: Veröffentlichen einer ClickOnce-Anwendung mit dem](../../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md) Webpublishing-Assistenten Gewusst wie: Angeben des Speicher Orts [der Dateien durch Visual Studio](../../deployment/how-to-specify-where-visual-studio-copies-the-files.md) Gewusst [wie: Angeben des Speicher Orts für die Installation durch Endbenutzer](../../deployment/how-to-specify-the-location-where-end-users-will-install-from.md) [ an: Geben Sie einen Link für den technischen Support](../../deployment/how-to-specify-a-link-for-technical-support.md) Gewusst [wie: Angeben des Offline-oder Online Installationsmodus von ClickOnce](../../deployment/how-to-specify-the-clickonce-offline-or-online-install-mode.md) Gewusst [wie: Aktivieren von AutoStart für CD-Installationen](../../deployment/how-to-enable-autostart-for-cd-installations.md) Gewusst wie: [Festlegen der ClickOnce-Veröffentlichungs Version](../../deployment/how-to-set-the-clickonce-publish-version.md) Gewusst [wie: Automatisches Inkrement an die ClickOnce-Veröffentlichungs Version](../../deployment/how-to-automatically-increment-the-clickonce-publish-version.md) [Gewusst wie: angeben, welche Dateien von ClickOnce veröffentlicht werden](../../deployment/how-to-specify-which-files-are-published-by-clickonce.md) Gewusst [wie: Installieren von erforderlichen Komponenten mit einer ClickOnce-Anwendung](../../deployment/how-to-install-prerequisites-with-a-clickonce-application.md) Gewusst wie: [Verwalten von Aktualisierungen für eine ClickOnce-Anwendung](../../deployment/how-to-manage-updates-for-a-clickonce-application.md) Gewusst [wie: Ändern des Veröffentlichungs Sprache für eine ClickOnce-Anwendung](../../deployment/how-to-change-the-publish-language-for-a-clickonce-application.md) Gewusst [wie: Angeben eines Startmenü namens für eine ClickOnce-Anwendung](../../deployment/how-to-specify-a-start-menu-name-for-a-clickonce-application.md) Gewusst [wie: Angeben einer Veröffentlichungs Seite für eine](../../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md) ClickOnce-Anwendung [ClickOnce-Sicherheit und-Bereitstellung](../../deployment/clickonce-security-and-deployment.md)
