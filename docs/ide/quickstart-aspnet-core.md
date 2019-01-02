---
title: Erstellen einer ASP.NET Core-Web-App in C#
description: Dieser Artikel enthält eine exemplarische Vorgehensweise zum Erstellen einer einfachen „Hallo Welt“-Web-App mit C# und ASP.NET Core.
ms.date: 10/29/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.custom: mvc,seodec18
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 23ba016d95e96965637ca6742501b09b16a42707
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684365"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App

In dieser 5-10-minütigen Einführung in die Bedienung von Visual Studio erstellen Sie eine einfache Hallo-Welt-Web-App unter Verwendung einer ASP.NET-Projektvorlage und der Programmiersprache C#.

## <a name="before-you-begin"></a>Bevor Sie beginnen

### <a name="install-visual-studio"></a>Installieren von Visual Studio

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

### <a name="update-visual-studio"></a>Aktualisieren von Visual Studio 2017

Wenn Sie Visual Studio bereits installiert haben, stellen Sie sicher, dass Sie die aktuelle Version verwenden. Weitere Informationen zum Aktualisieren Ihrer Installation finden Sie auf der Seite [Aktualisieren von Visual Studio 2017 auf die aktuelle Version](../install/update-visual-studio.md).

### <a name="choose-your-theme-optional"></a>Auswählen eines Designs (optional)

Die Screenshots in diesem Schnellstarttutorial verwenden das dunkle Design. Wenn Sie ebenfalls das dunkle Design verwenden möchten, finden Sie auf der Seite [Personalisieren der Visual Studio-IDE und des Editors](quickstart-personalize-the-ide.md) entsprechende Anweisungen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die ASP.NET Core-Webanwendung erstellen. Der Projekttyp enthält alle nötigen Vorlagendateien zum Erstellen einer Web-App, schon bevor Sie mit der Bearbeitung beginnen.

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Klappen Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** auf, und wählen Sie **.NET Core** aus. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Web-App**. Benennen Sie Ihre Datei anschließend mit `HelloWorld` und wählen Sie **OK**.

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

1. Klicken Sie im oberen Dropdownmenü des Dialogfelds **Neue ASP.NET Core-Webanwendung** auf **ASP.NET Core 2.0** (oder höher).

   > [!NOTE]
   > Wenn **ASP.NET Core 2.0** (oder höher) nicht angezeigt wird, stellen Sie sicher, dass Sie die aktuelle Version von Visual Studio ausführen. Weitere Informationen zum Aktualisieren Ihrer Installation finden Sie auf der Seite [Aktualisieren von Visual Studio 2017 auf die aktuelle Version](../install/update-visual-studio.md).

1. Wählen Sie dann **Webanwendung** und anschließend **OK** aus.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](../ide/media/quickstart-aspnet-core20.png)

Im Anschluss wird Ihre Projektdatei in Visual Studio geöffnet.

## <a name="create-the-app"></a>Erstellen der App

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner **Seiten**, und wählen Sie die **About.cshtml**.

   ![Auswählen der About-cshtml-Datei im Projektmappen-Explorer](../ide/media/csharp-aspnet-about-page-html-file.png)

   Diese Datei entspricht der Seite mit der Bezeichnung **Info** in der Webanwendung.

   ![Die Seite „Info“ in der Web-App](../ide/media/csharp-aspnet-about-page.png)

   Im Editor wird der HTML-Code für den Bereich „Weitere Informationen“ der Seite **Info** angezeigt.

   ![HTML-Code für den Bereich „Weitere Informationen“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-page.png)

1. Ändern Sie den Text "„Weitere Informationen“ in „**Hallo Welt!**“.

   ![Ändern des standardmäßigen HTML-Codes für den Bereich „Weitere Informationen“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-page-hello-world.png)

1. Erweitern Sie im **Projektmappen-Explorer** den Ordner **About.cshtml**, und wählen Sie die **About.cshtml.cs**. (Diese Datei entspricht auch der Seite **Info** in Ihrer Web-App.)

   ![Auswählen der About-cshtml-Datei im Projektmappen-Explorer](../ide/media/csharp-aspnet-about-page-code-file.png)

   Im Editor wird C#-Code mit Text für den Bereich „Anwendungsbeschreibung“ der Seite **Info** angezeigt.

   ![C#-Code für die Anwendung im Bereich „Anwendungsbeschreibung“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-cs-code.png)

1. Ändern Sie den Text „Anwendungsbeschreibung“ in „**Wie lautet meine Nachricht?**“.

   ![Ändern des Standardnachrichtentexts im Bereich „Anwendungsbeschreibung“ im Visual Studio-Editor](../ide/media/csharp-aspnet-about-cshtml-cs-message.png)

## <a name="run-the-app"></a>Ausführen der App

1. Drücken Sie **STRG**+**F5**, um die App auszuführen und sie im Webbrowser zu öffnen.

   > [!NOTE]
   > Wenn Sie die Fehlermeldung **Verbindung mit Webserver „IIS Express“ nicht möglich** erhalten oder eine Fehlermeldung angezeigt wird, in der ein SSL-Zertifikat erwähnt wird, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio unter Verwendung der Option **Als Administrator ausführen** aus dem Kontextmenü. Führen Sie die Anwendung anschließend erneut aus.

1. Wählen Sie im oberen Bereich der Webseite **Info** aus.

   ![Auswählen von „Info“ auf der Webseite](../ide/media/csharp-aspnet-home-page-about.png)

1. Schauen Sie sich den aktualisierten Text an, den Sie auf der Seite **Info** hinzugefügt haben.

   ![Anzeigen der aktualisierten „Info“-Seite mit dem hinzugefügten Text](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Schließen Sie den Webbrowser.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE (Integrierte Entwicklungsumgebung) gelernt haben.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Erste Schritte mit C# und ASP.NET in Visual Studio](../get-started/csharp/tutorial-aspnet-core.md)

## <a name="see-also"></a>Siehe auch

[Veröffentlichen Ihrer Web-App in Azure App Service mit Visual Studio](../deployment/quickstart-deploy-to-azure.md)
