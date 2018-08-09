---
title: Verwenden von Visual Studio zum Erstellen einer ASP.NET Core-Web-App in C#
description: Dieser Artikel enthält eine ausführliche Anleitung zum Erstellen einer ASP.NET Core-Web-App mit C# in Visual Studio.
ms.custom: mvc
ms.date: 07/20/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: quickstart
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: a64674ae5a902e332ae8b9eb3cbe6a22d09a1133
ms.sourcegitcommit: 495bba1d8029646653f99ad20df2f80faad8d58b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/31/2018
ms.locfileid: "39380615"
---
# <a name="quickstart-use-visual-studio-to-create-your-first-aspnet-core-web-app"></a>Schnellstart: Verwenden von Visual Studio zum Erstellen Ihrer ersten ASP.NET Core-Web-App

In dieser 5-10-minütigen Einführung in die Bedienung von Visual Studio erstellen Sie eine einfache Hallo-Welt-Web-App unter Verwendung einer ASP.NET-Projektvorlage und der Programmiersprache C#.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst müssen Sie ein Projekt für die ASP.NET Core-Webanwendung erstellen. Der Projekttyp enthält alle nötigen Vorlagendateien zum Erstellen einer Web-App, schon bevor Sie mit der Bearbeitung beginnen.

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**.

1. Klappen Sie im linken Bereich des Dialogfelds **Neues Projekt** den Eintrag **Visual C#** auf, und wählen Sie **.NET Core** aus. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Web-App**. Benennen Sie Ihre Datei anschließend mit `HelloWorld` und wählen Sie **OK**.

   ![Erstellen des neuen Projekts für die ASP.NET Core-Web-App für C#](../ide/media/csharp-aspnet-choose-template-name-file.png)

   > [!NOTE]
   > Falls Sie die Projektvorlagenkategorie **.NET Core** nicht finden, klicken Sie im linken Bereich auf den Link **Visual Studio-Installer öffnen**.
   >
   > ![Den Visual Studio-Installer im Dialogfeld „Neues Projekt“ öffnen](../ide/media/open-visual-studio-installer.png)
   >
   > Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.
   >
   > ![ASP.NET-Workload in VS-Installer](../ide/media/quickstart-aspnet-workload.png)
   >
   > (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

1. Überprüfen Sie im oberen Dropdownmenü des Dialogfelds **Neue ASP.NET Core-Webanwendung**, ob **ASP.NET Core 2.0** angezeigt wird. Wählen Sie dann **Webanwendung** und anschließend **OK** aus.

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
   > Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver „IIS Express“ hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.

1. Wählen Sie im oberen Bereich der Webseite **Info** aus.

   ![Auswählen von „Info“ auf der Webseite](../ide/media/csharp-aspnet-home-page-about.png)

1. Schauen Sie sich den aktualisierten Text an, den Sie auf der Seite **Info** hinzugefügt haben.

   ![Anzeigen der aktualisierten „Info“-Seite mit dem hinzugefügten Text](../ide/media/csharp-aspnet-about-page-hello-world.png)

1. Schließen Sie den Webbrowser.

Damit haben Sie den Schnellstart erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE (Integrierte Entwicklungsumgebung) gelernt haben.

## <a name="next-steps"></a>Nächste Schritte

Fahren Sie für weitere Informationen mit dem folgenden Tutorial fort:

> [!div class="nextstepaction"]
> [Erste Schritte mit C# und ASP.NET in Visual Studio](tutorial-csharp-aspnet-core.md)
>
> [!div class="nextstepaction"]
> [Erste Schritte mit ASP.NET Core MVC und Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)

## <a name="see-also"></a>Siehe auch

[Veröffentlichen Ihrer Web-App in Azure App Service mit Visual Studio](..//deployment/quickstart-deploy-to-azure.md)
