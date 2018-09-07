---
title: Erste Schritte mit C# und ASP.NET Core in Visual Studio
description: Dieser Artikel enthält eine ausführliche Anleitung zum Erstellen einer ASP.NET Core-Web-App mit C# in Visual Studio.
ms.custom: ''
ms.date: 08/10/2018
ms.prod: visual-studio-dev15
ms.technology: vs-acquisition
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: douge
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: fb1532a76d9bc530146ba5a0f563bcaa9389226c
ms.sourcegitcommit: db94ca7a621879f98d4c6aeefd5e27da1091a742
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/13/2018
ms.locfileid: "42626529"
---
# <a name="tutorial-get-started-with-c-and-aspnet-core-in-visual-studio"></a>Tutorial: Erste Schritte mit C# und ASP.NET Core in Visual Studio

In diesem Tutorial für die C#-Entwicklung mit ASP.NET Core in Visual Studio werden wir eine C#-ASP.NET Core-Web-App erstellen, Änderungen vornehmen, einige Funktionen der IDE kennenlernen und die App ausführen.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2017) kostenlos herunterladen.

## <a name="create-a-project"></a>Erstellen eines Projekts

Zunächst erstellen Sie ein ASP.NET Core-Projekt. Schon bevor Sie mit der Bearbeitung beginnen enthält der Projekttyp bereits alle Vorlagendateien, die Sie für eine Website benötigen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt**. 

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#** und anschließend **Web**, und klicken Sie auf **.NET Core**. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Web-App**. Nennen Sie die Datei *MyCoreApp*, und klicken Sie auf **OK**.

   ![Projektvorlage „ASP.NET Core-Webanwendung“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/csharp-aspnet-choose-template-name-mycoreapp-mvc.png)

### <a name="add-a-workload-optional"></a>Hinzufügen einer Workload (optional)

Wenn Ihnen die Projektvorlage **ASP.NET Core-Webanwendung** fehlt, fügen Sie einfach die Workload **ASP.NET und Webentwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

#### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Über das Dialogfeld „Neues Projekt“

1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**.

   ![Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/vs-open-visual-studio-installer-generic.png)

1. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/quickstart-aspnet-workload.png)

   (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

#### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Über die Menüleiste „Extras“

1. Schließen Sie das Dialogfeld **Neues Projekt**. Wählen Sie dann in der oberen Menüleiste **Extras** > **Get Tools and Features** (Tools und Features abrufen) aus.

1. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   (Möglicherweise müssen Sie Visual Studio schließen, bevor Sie die Installation des neuen Workloads fortsetzen können.)

### <a name="add-a-project-template"></a>Hinzufügen einer Projektvorlage

1. Klicken Sie im Dialogfeld **Neue ASP.NET Core-Webanwendung** auf die Projektvorlage **Webanwendung (Model-View-Controller)**.

1. Überprüfen Sie, ob **ASP.NET Core 2.0** im oberen Dropdownmenü angezeigt wird. Klicken Sie dann auf **OK**.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Die Projektmappe

In dieser Projektmappe wurde das Architekturmodell „Model-View-Controller (MVC)“ angewandt, bei dem eine App in drei Hauptkomponenten unterteilt wird:

* **Modelle** enthalten Klassen, die die Daten der App darstellen. Die Modellklassen verwenden Validierungslogik zum Erzwingen von Geschäftsregeln für diese Daten. In der Regel wird der Modellstatus von Modellobjekten in einer Datenbank abgerufen und gespeichert.
* **Ansichten** sind die Komponenten, die die Benutzeroberfläche der App anzeigen. Im Allgemeinen werden die Modelldaten auf dieser Benutzeroberfläche angezeigt.
* **Controller** umfassen Klassen, die Browseranforderungen verarbeiten. Sie rufen Modelldaten ab und rufen Ansichtsvorlagen auf, die eine Antwort zurückgeben. In einer MVC-Anwendung zeigt die Ansicht nur die Informationen. Die Benutzereingaben und -interaktionen werden vom Controller beantwortet und verarbeitet.

Mithilfe des MVC-Modells können Sie Apps erstellen, die leichter zu testen und zu aktualisieren sind als herkömmliche monolithische Apps.

## <a name="tour-your-solution"></a>Kennenlernen der Projektmappe

 1. Die Projektvorlage erstellt eine Projektmappe mit einem einzelnen ASP.NET Core-Projekt namens **MyCoreApp**. Erweitern Sie den Projektknoten, um seinen Inhalt anzuzeigen.

    ![ASP.NET-Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp-mvc.png)

 1. Öffnen Sie im Ordner **Controller** die Datei *HomeController.cs*.

     ![Datei „HomeController.cs“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

 1. Rufen Sie die Datei *HomeController.cs* auf.

     ![„HomeController.cs“ im Visual Studio-Codefenster](../ide/media/csharp-aspnet-home-controller-code.png)

 1. Das Projekt hat auch einen Ordner **Sichten**, der andere Ordner enthält, die den Controllern entsprechen. Die CSHTML-Ansichtsdatei (eine Erweiterung von HTML) des Pfads */Home/About* wäre z.B. *Views/Home/About.cshtml*. Öffnen Sie diese Datei.

     ![Datei „About.cshtml“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

    Diese CSHTML-Datei verwendet die Razor-Syntax, um HTML auf der Grundlage einer Kombination von Standardtags und Inline-C# zu rendern.

     ![„About.cshtml“ im Visual Studio-Codefenster](../ide/media/csharp-aspnet-about-cshtml-code.png)

    >[!NOTE]
    > Weitere Informationen hierzu finden Sie auf der Seite [Einführung in die ASP.NET-Webprogrammierung mithilfe der Razor-Syntax (C#)](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

 1. Dieses Projekt enthält auch den Ordner **wwwroot**, der das Stammverzeichnis Ihrer Website ist. Erweitern Sie den Ordner, um den Inhalt anzuzeigen.

     ![Ordner „wwwroot“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

    Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in die gewünschten Pfade einfügen.

 1. Es gibt auch verschiedene Konfigurationsdateien, mit denen das Projekt, die Pakete und die Anwendung zur Laufzeit verwaltet werden können. Die [Standardkonfiguration](/aspnet/core/fundamentals/configuration) der Anwendung befindet sich z.B. in der Datei *appsettings.json*. Sie können diese Einstellungen jedoch auch mit *appsettings.Development.json* überschreiben. Erweitern Sie die Datei **appsettings.json**, um die Datei **appsettings.Development.json** anzuzeigen.

     ![Konfigurationsdateien im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-debug-and-make-changes"></a>Ausführen, Debuggen und Vornehmen von Änderungen

1. Klicken Sie in der IDE auf die Schaltfläche **IIS Express**, um die App im Debugmodus zu erstellen und auszuführen. (Alternativ können Sie **F5** drücken oder in der Menüleiste auf **Debuggen > Debuggen starten** klicken.)

     ![Die Schaltfläche „IIS Express“ in Visual Studio](../ide/media/csharp-aspnet-iis-express-button.png)

     > [!NOTE]
     > Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver "IIS Express" hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.

1. Visual Studio startet ein Browserfenster. Klicken Sie auf **About** (Info).

   ![„About“ im Browserfenster für die App auswählen](../ide/media/csharp-aspnet-browser-page.png)

   Auf der Seite **About** im Browser wird u.a. der Text gerendert, der in der Datei *HomeController.cs* festgelegt ist.

   ![Text auf der Seite „About“](../ide/media/csharp-aspnet-browser-page-about.png)

1. Lassen Sie das Browserfenster geöffnet, und kehren Sie zu Visual Studio zurück. Öffnen Sie *Controllers/HomeController.cs*, wenn es nicht bereits geöffnet ist.

   ![Datei „HomeController.cs“ über den Projektmappen-Explorer in Visual Studio öffnen](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Legen Sie in der ersten Zeile der Methode **About** einen Haltepunkt fest. Klicken Sie dazu auf den Rand, oder setzen Sie den Cursor in die Zeile, und drücken Sie **F9**.

   Diese Zeile legt einige Daten der Auflistung **ViewData** fest, die auf der CSHTML-Seite unter *Views/Home/About.cshtml* gerendert wird.

   ![Legen Sie einen Haltepunkt in der ersten Zeile der „About“-Methode in „About.cshtml“ fest.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Kehren Sie zum Browser zurück, und aktualisieren Sie die Seite **About**. Dadurch wird der Haltepunkt in Visual Studio ausgelöst.

1. Zeigen Sie in Visual Studio auf den Member **ViewData**, um dessen Daten anzuzeigen.

   ![Member „ViewData“ der „About“-Methode für weitere Informationen anzeigen](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Entfernen Sie den Anwendungshaltepunkt mit derselben Methode, mit der Sie ihn hinzugefügt haben.

1. Öffnen Sie *Views/Home/About.cshtml*.

   ![Klicken Sie im Projektmappen-Explorer auf „About.cshtml“.](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Ändern Sie den Text **additional** in **changed**, und speichern Sie die Datei.

   ![Text „additional“ in „changed“ ändern](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Kehren Sie zum Browserfenster zurück, um den aktualisierten Text zu prüfen. (Aktualisieren Sie den Browser, wenn der neue Text nicht angezeigt wird.)

    ![Browserfenster aktualisieren, um den neuen Text anzuzeigen](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Klicken Sie in der Symbolleiste auf die Schaltfläche **Debuggen beenden**. (Alternativ können Sie **UMSCHALTTASTE**+**F5** drücken oder in der Menüleiste auf **Debuggen** > **Debuggen beenden** klicken.)

   ![Schaltfläche „Debuggen beenden“](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="quick-answers-faq"></a>Schnelle Antworten zu häufig gestellten Fragen

In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte besprochen.

### <a name="what-is-c"></a>Was ist C#?

[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) ist eine typsichere und objektorientierte Programmiersprache, die nicht nur stabil, sondern auch einfach zu erlernen ist.

### <a name="what-is-aspnet-core"></a>Was ist ASP.NET Core?

ASP.NET Core ist ein plattformübergreifendes Open Source-Framework zum Erstellen von Anwendungen mit Internetverbindung, wie etwa Web-Apps und -dienste. ASP.NET Core-Apps können unter .NET Core oder .NET Framework ausgeführt werden. Sie können Ihre ASP.NET Core-Apps plattformübergreifend unter Windows, macOS und Linux ausführen und entwickeln. ASP.NET Core ist auf [GitHub](https://github.com/aspnet/home) verfügbar.

### <a name="what-is-visual-studio"></a>Was ist Visual Studio?

Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE gelernt haben. Weitere Informationen zum Erstellen einer Web-App oder Website mit C# und ASP.NET Core finden Sie in den folgenden Tutorials:

> [!div class="nextstepaction"]
> [Erste Schritte mit ASP.NET Core MVC und Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?view=aspnetcore-2.1&tabs=aspnetcore2x)
>
> [!div class="nextstepaction"]
> [Erstellen einer Razor-Seiten-Web-App mit ASP.NET Core](/aspnet/core/tutorials/razor-pages/?view=aspnetcore-2.1)

## <a name="see-also"></a>Siehe auch

[Veröffentlichen Ihrer Web-App in Azure App Service mit Visual Studio](..//deployment/quickstart-deploy-to-azure.md)