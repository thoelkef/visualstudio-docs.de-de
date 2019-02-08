---
title: Erstellen einer ASP.NET Core-Web-App in C#
description: Dieser Artikel enthält eine exemplarische Vorgehensweise zum Erstellen einer einfachen „Hallo Welt“-Web-App mit C# und ASP.NET Core.
ms.date: 02/01/2019
ms.prod: visual-studio-dev15
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 61bfe7dfa42542199f3773d1587d0e10ec315f98
ms.sourcegitcommit: 612f8c21d1448f1a013c30100cdecfbec5ddb24f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2019
ms.locfileid: "55571147"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App

In dieser 5-10-minütigen Einführung in die Bedienung von Visual Studio erstellen Sie eine einfache Hallo-Welt-Web-App unter Verwendung einer ASP.NET-Projektvorlage und der Programmiersprache C#.

## <a name="before-you-begin"></a>Bevor Sie beginnen

### <a name="install-visual-studio"></a>Installieren von Visual Studio

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2017) kostenlos herunterladen.

### <a name="choose-your-theme-optional"></a>Auswählen eines Designs (optional)

Die Screenshots in diesem Schnellstarttutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](quickstart-personalize-the-ide.md) entsprechende Anweisungen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die ASP.NET Core-Webanwendung erstellen. Der Projekttyp enthält alle nötigen Vorlagendateien zum Erstellen einer Web-App, schon bevor Sie mit der Bearbeitung beginnen.

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Klappen Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** auf, und wählen Sie **.NET Core** aus. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Web-App**. <br/><br/>Benennen Sie Ihre Datei anschließend mit `HelloWorld` und wählen Sie **OK**.

   ![Erstellen des neuen Projekts für die ASP.NET Core-Web-App für C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Falls Sie die Projektvorlagenkategorie **.NET Core** nicht finden, klicken Sie im linken Bereich auf den Link **Visual Studio-Installer öffnen**. (Abhängig von Ihren Anzeigeeinstellungen müssen Sie zur Anzeige möglicherweise scrollen.)
   >
   > ![Den Visual Studio-Installer im Dialogfeld „Neues Projekt“ öffnen](../ide/media/open-visual-studio-installer.png)
   >
   > Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.
   >
   > ![ASP.NET-Workload in VS-Installer](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

1. Klicken Sie im oberen Dropdownmenü des Dialogfelds **Neue ASP.NET Core-Webanwendung** auf **ASP.NET Core 2.1**. Wählen Sie dann **Webanwendung** und anschließend **OK** aus.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](../ide/media/aspnet-core-2dot1.png)

   > [!NOTE]
   > Wenn **ASP.NET Core 2.1** (oder höher) nicht angezeigt wird, stellen Sie sicher, dass Sie die aktuelle Version von Visual Studio ausführen. Weitere Informationen zum Aktualisieren Ihrer Installation finden Sie auf der Seite [Aktualisieren von Visual Studio 2017 auf die aktuelle Version](../install/update-visual-studio.md).

Im Anschluss wird Ihre Projektdatei in Visual Studio geöffnet.

## <a name="create-and-run-the-app"></a>Erstellen und Ausführen der App

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner **Seiten**, und wählen Sie die **About.cshtml**.

   ![Auswählen der About-cshtml-Datei im Projektmappen-Explorer](../ide/media/csharp-aspnet-about-page-html-file.png)

   Diese Datei entspricht der Seite mit der Bezeichnung **Info** in der Web-App, die im Webbrowser ausgeführt wird.

   ![Die Seite „Info“ in der Web-App](../ide/media/csharp-aspnet-about-page.png)

   Im Editor wird der HTML-Code für den Bereich „Weitere Informationen“ der Seite **Info** angezeigt.

   ![HTML-Code für den Bereich „Weitere Informationen“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Ändern Sie den Text "„Weitere Informationen“ in „**Hallo Welt!**“.

   ![Ändern des standardmäßigen HTML-Codes für den Bereich „Weitere Informationen“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner **About.cshtml**, und wählen Sie die **About.cshtml.cs**. (Diese Datei entspricht auch der Seite **Info** in einem Webbrowser.)

   ![Auswählen der About-cshtml-Datei im Projektmappen-Explorer](../ide/media/csharp-aspnet-about-page-code-file.png)

   Im Editor wird C#-Code mit Text für den Bereich „Anwendungsbeschreibung“ der Seite **Info** angezeigt.

   ![C#-Code für die Anwendung im Bereich „Anwendungsbeschreibung“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Ändern Sie den Text „Anwendungsbeschreibung“ in „**Wie lautet meine Nachricht?**“.

   ![Ändern des Standardnachrichtentexts im Bereich „Anwendungsbeschreibung“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

1. Klicken Sie auf **IIS Express**, oder drücken Sie **STRG**+**F5**, um die App auszuführen und im Webbrowser zu öffnen.

   ![Die Schaltfläche „IIS Express“ in Visual Studio](../ide/media/csharp-aspnet-helloworld-iisbutton.png)

   > [!NOTE]
   > Wenn Sie die Fehlermeldung **Verbindung mit Webserver „IIS Express“ nicht möglich** erhalten oder eine Fehlermeldung angezeigt wird, in der ein SSL-Zertifikat erwähnt wird, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio unter Verwendung der Option **Als Administrator ausführen** aus dem Kontextmenü. Führen Sie die Anwendung anschließend erneut aus.

1. Überprüfen Sie im Webbrowser, ob auf der Seite **Info** Ihr aktualisierter Text angezeigt wird.

   ![Anzeigen der aktualisierten „Info“-Seite mit den gemachten Änderungen](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Schließen Sie den Webbrowser.

### <a name="review-your-work"></a>Überprüfen Ihrer Arbeit

Sehen Sie sich die folgende Animation an, um Ihre Arbeit zu überprüfen, die Sie im Rahmen des vorherigen Abschnitts verrichtet haben.

  ![Animierte GIF-Datei, auf der gezeigt wird, wie eine einfache C#-ASP.NET Core-Web-App in Visual Studio erstellt und ausgeführt wird](../ide/media/csharp-aspnet-animated-hello-world.gif)

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE (Integrierte Entwicklungsumgebung) gelernt haben.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Erste Schritte mit C# und ASP.NET in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Siehe auch

[Veröffentlichen Ihrer Web-App in Azure App Service mit Visual Studio](../deployment/quickstart-deploy-to-azure.md)
