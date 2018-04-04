---
title: Erste Schritte mit C# und ASP.NET Core in Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 12/11/2017
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: tutorial
ms.devlang: CSharp
author: TerryGLee
ms.author: tglee
manager: ghogen
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: 9a24ccbcecc2d5bd4d5799ada048fee0004514f7
ms.sourcegitcommit: e01ccb5ca4504a327d54f33589911f5d8be9c35c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/15/2018
---
# <a name="getting-started-with-c-and-aspnet-in-visual-studio"></a>Erste Schritte mit C# und ASP.NET Core in Visual Studio
In diesem Tutorial für die C#-Entwicklung mit ASP.NET Core in Visual Studio werden wir eine C#-ASP.NET Core-Web-App erstellen, Code hinzufügen, einige Funktionen der IDE kennenlernen und die App ausführen.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es auf der Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen.

## <a name="before-you-begin"></a>Bevor Sie beginnen
In den folgenden häufig gestellten Fragen werden einige wichtige Konzepte vorgestellt.
### <a name="what-is-c"></a>Was ist C#?
[C#](/dotnet/csharp/getting-started/introduction-to-the-csharp-language-and-the-net-framework) ist eine typsichere und objektorientierte Programmiersprache, die nicht nur stabil, sondern auch einfach zu erlernen ist.
### <a name="what-is-aspnet-core"></a>Was ist ASP.NET Core?
ASP.NET Core ist ein plattformübergreifendes Open Source-Framework zum Erstellen von Anwendungen mit Internetverbindung, wie etwa Web-Apps und -dienste. ASP.NET Core-Apps können unter .NET Core oder .NET Framework ausgeführt werden. Sie können Ihre ASP.NET Core-Apps plattformübergreifend unter Windows, macOS und Linux ausführen und entwickeln. ASP.NET Core ist auf [GitHub](https://github.com/aspnet/home) verfügbar.
### <a name="what-is-visual-studio"></a>Was ist Visual Studio?
Visual Studio ist eine integrierte Zusammenstellung von Entwicklertools, die die Produktivität fördern. Es ist also ein Programm zum Erstellen von Programmen und Anwendungen.  

## <a name="start-developing"></a>Mit dem Entwickeln beginnen
Sind Sie bereit? Los geht‘s!

### <a name="create-a-project"></a>Erstellen eines Projekts
Zunächst erstellen Sie ein ASP.NET Core-Projekt. Der Projekttyp enthält schon bevor Sie mit der Bearbeitung beginnen alle Vorlagendateien, die Sie benötigen.

1. Öffnen Sie Visual Studio 2017.

2. Klicken Sie in der Menüleiste im oberen Bereich auf **Datei** > **Neu** > **Projekt...**.

3. Erweitern Sie im Dialogfeld **Neues Projekt** links den Eintrag **Visual C#** und anschließend **Web**, und klicken Sie auf **.NET Core**. Klicken Sie im mittleren Bereich auf **ASP.NET Core-Webanwendung**, nennen Sie die erste Datei *MyCoreApp*, und klicken Sie anschließend auf **OK**.   

   ![Projektvorlage „ASP.NET Core-Webanwendung“ im Dialogfeld „Neues Projekt“ in der Visual Studio-IDE](../ide/media/new-project-csharp-aspnet-mycoreapp.png)

#### <a name="add-a-workload-optional"></a>Hinzufügen einer Workload (optional)
Wenn Ihnen die Projektvorlage **ASP.NET Core-Webanwendung** fehlt, fügen Sie einfach die Workload **ASP.NET und Webentwicklung** hinzu. Sie haben folgende Möglichkeiten für das Hinzufügen der Workload, je nachdem, welche Visual Studio 2017-Updates auf dem Computer installiert sind.

##### <a name="option-1-use-the-new-project-dialog-box"></a>Option 1: Über das Dialogfeld „Neues Projekt“
1. Klicken Sie im Dialogfeld **Neues Projekt** im linken Bereich auf den Link **Visual Studio-Installer öffnen**.

  ![Klicken Sie auf den Link „Visual Studio-Installer öffnen“ im Dialogfeld „Neues Projekt“](../ide/media/vs-open-visual-studio-installer-generic.png)

2. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.

   ![Workload für die plattformübergreifende .NET Core-Entwicklung im Visual Studio-Installer](../ide/media/asp-dot-net-web-dev-workload.png)

##### <a name="option-2-use-the-tools-menu-bar"></a>Option 2: Über die Menüleiste „Extras“
1. Schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie in der Menüleiste oben auf **Extras** > **Tools und Features abrufen…**.

2. Der Visual Studio-Installer wird gestartet. Klicken Sie auf die Workload **ASP.NET und Webentwicklung** und anschließend auf **Ändern**.   

#### <a name="add-a-project-template"></a>Hinzufügen einer Projektvorlage
1. Klicken Sie im Dialogfeld **Neue ASP.NET Core-Webanwendung** auf die Projektvorlage **Webanwendung (Model-View-Controller)**.  

2. Wählen Sie aus dem oberen Dropdownmenü **ASP.NET Core 2.0** aus. (Wenn **ASP.NET Core 2.0** nicht in der Liste angezeigt wird, installieren Sie es über den **Download**-Link, der in einer gelben Leiste im oberen Bereich des Dialogfelds angezeigt werden sollte.) Klicken Sie auf **OK**.

   ![Dialogfeld „Neue ASP.NET Core-Webanwendung“](../ide/media/new-project-csharp-aspnet-web-app-mvc.png)

### <a name="about-your-solution"></a>Die Projektmappe
In dieser Projektmappe wurde das Architekturmodell „Model-View-Controller (MVC)“ angewandt, bei dem eine App in drei Hauptkomponenten unterteilt wird:

* **Modelle** enthalten Klassen, die die Daten der App darstellen. Die Modellklassen verwenden Validierungslogik zum Erzwingen von Geschäftsregeln für diese Daten. In der Regel wird der Modellstatus von Modellobjekten in einer Datenbank abgerufen und gespeichert.
* **Ansichten** sind die Komponenten, die die Benutzeroberfläche der App anzeigen. Im Allgemeinen werden die Modelldaten auf dieser Benutzeroberfläche angezeigt.
* **Controller** umfassen Klassen, die Browseranforderungen verarbeiten. Sie rufen Modelldaten ab und rufen Ansichtsvorlagen auf, die eine Antwort zurückgeben. In einer MVC-Anwendung zeigt die Ansicht nur die Informationen. Die Benutzereingaben und -interaktionen werden vom Controller beantwortet und verarbeitet.

Mithilfe des MVC-Modells können Sie Apps erstellen, die leichter zu testen und zu aktualisieren sind als herkömmliche monolithische Apps.

### <a name="tour-your-solution"></a>Kennenlernen der Projektmappe
1. Die Projektvorlage erstellt eine Projektmappe mit einem einzelnen ASP.NET Core-Projekt namens **MyCoreApp**. Erweitern Sie den Projektknoten, um seinen Inhalt anzuzeigen.

    ![ASP.NET-Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-mycoreapp.png)

1. Öffnen Sie im Ordner **Controller** die Datei **HomeController.cs**.

      ![Datei „HomeController.cs“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

2. Sehen Sie sich den Inhalt von **HomeController.cs** an.

  ![„HomeController.cs“ im Visual Studio-Codefenster](../ide/media/csharp-aspnet-home-controller-code.png)

4. Das Projekt hat auch einen Ordner **Views** (Ansichten), der andere Ordner enthält, die den Controllern entsprechen, sowie einen namens **Shared** (Freigegeben). Die CSHTML-Ansichtsdatei (eine Erweiterung von HTML) des Pfads **/Home/About** wäre z.B. **Views/Home/About.cshtml**. Öffnen Sie diese Datei.

  ![Datei „About.cshtml“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

5. Diese CSHTML-Datei verwendet die Razor-Syntax, um HTML auf der Grundlage einer Kombination von Standardtags und Inline-C# zu rendern.

  ![„About.cshtml“ im Visual Studio-Codefenster](../ide/media/csharp-aspnet-about-cshtml-code.png)

 >[!NOTE]
 > Weitere Informationen hierzu finden Sie unter [Einführung in die ASP.NET-Webprogrammierung mithilfe der Razor-Syntax (C#)](/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

6. Diese Projektmappe enthält auch den Ordner **wwwroot**, der das Stammverzeichnis Ihrer Website ist. Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in den Pfaden einfügen, in denen sie sich bei der Bereitstellung der Website befinden sollen.

 ![Ordner „wwwroot“ im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-wwwroot.png)

7. Es gibt auch verschiedene Konfigurationsdateien, mit denen Projekte einschließlich der Pakete und die Anwendung zur Laufzeit verwaltet werden können. Die [Standardkonfiguration](/aspnet/core/fundamentals/configuration) der Anwendung befindet sich z.B. in der Datei **appsettings.json**. Sie können jedoch einige bzw. alle diese Einstellungen umgebungsabhängig überschreiben, d.h. beispielsweise die Datei **appSettings.Development.json** für die Umgebung **Entwicklung** bereitstellen.

 ![Konfigurationsdateien im Projektmappen-Explorer in Visual Studio](../ide/media/csharp-aspnet-solution-explorer-config-files.png)

## <a name="run-and-debug-the-application"></a>Ausführen und Debuggen der Anwendung

1. Klicken Sie in der IDE auf die Schaltfläche **IIS Express**, um die App im Debugmodus zu erstellen und auszuführen. (Alternativ können Sie **F5** drücken oder in der Menüleiste auf **Debuggen > Debuggen starten** klicken.)

  ![Auf die Schaltfläche „IIS Express“ in Visual Studio klicken](../ide/media/csharp-aspnet-iis-express-button.png)

  > [!NOTE]
  > Wenn Sie die Fehlermeldung **Es kann keine Verbindung mit dem Webserver "IIS Express" hergestellt werden.** erhalten, schließen Sie Visual Studio. Öffnen Sie dann Visual Studio, indem Sie im Kontextmenü auf die Option **Als Administrator ausführen** klicken. Führen Sie die Anwendung anschließend erneut aus.

1. Visual Studio startet ein Browserfenster. Klicken Sie auf **About** (Info).

 ![„About“ im Browserfenster für die App auswählen](../ide/media/csharp-aspnet-browser-page.png)

 Auf der Seite „About“ im Browser wird u.a. der Text gerendert, der in der Datei „HomeController.cs“ festgelegt ist.

   ![Text auf der Seite „About“](../ide/media/csharp-aspnet-browser-page-about.png)

1. Lassen Sie das Browserfenster geöffnet, und kehren Sie zu Visual Studio zurück. Öffnen Sie **Controllers/HomeController.cs**, wenn es nicht bereits geöffnet ist.

 ![Datei „HomeController.cs“ über den Projektmappen-Explorer in Visual Studio öffnen](../ide/media/csharp-aspnet-solution-explorer-home-controller.png)

1. Legen Sie in der ersten Zeile der Methode **About** einen Haltepunkt fest. Klicken Sie dazu auf den Rand, oder setzen Sie den Cursor in die Zeile, und drücken Sie **F9**.

  Diese Zeile legt einige Daten der Auflistung **ViewData** fest, die auf der CSHTML-Seite unter **Views/Home/About.cshtml** gerendert wird.

 ![Legen Sie einen Haltepunkt in der ersten Zeile der „About“-Methode in „About.cshtml“ fest.  ](../ide/media/csharp-aspnet-home-controller-code-set-breakpoint.png)

1. Kehren Sie zum Browser zurück, und aktualisieren Sie die Seite „About“. Dadurch wird der Haltepunkt in Visual Studio ausgelöst.

1. Zeigen Sie in Visual Studio auf den Member **ViewData**, um dessen Daten anzuzeigen.

 ![Member „ViewData“ der „About“-Methode für weitere Informationen anzeigen](../ide/media/csharp-aspnet-home-controller-view-breakpoint-info.png)

1. Entfernen Sie den Anwendungshaltepunkt mit derselben Methode, mit der Sie ihn hinzugefügt haben.

1. Öffnen Sie **Views/Home/About.cshtml**.

 ![Klicken Sie im Projektmappen-Explorer auf „About.cshtml“.](../ide/media/csharp-aspnet-solution-explorer-view-about.png)

1. Ändern Sie den Text **additional** in **changed**, und speichern Sie die Datei.

 ![Text „additional“ in „changed“ ändern](../ide/media/csharp-aspnet-about-cshtml-code-change.png)

1. Kehren Sie zum Browserfenster zurück, um den aktualisierten Text zu prüfen. (Aktualisieren Sie den Browser, wenn der neue Text nicht angezeigt wird.)

  ![Browserfenster aktualisieren, um den neuen Text anzuzeigen](../ide/media/csharp-aspnet-browser-page-about-changed.png)

1. Klicken Sie in der Symbolleiste auf die Schaltfläche **Debuggen beenden**. (Alternativ können Sie **UMSCHALTTASTE**+**F5** drücken oder in der Menüleiste auf **Debuggen** > **Debuggen beenden** klicken.)

 ![In der Symbolleiste auf die Schaltfläche „Debuggen beenden“ klicken](../ide/media/csharp-aspnet-stop-debugging.png)

## <a name="next-steps"></a>Nächste Schritte

Damit haben Sie das Tutorial erfolgreich abgeschlossen. Wir hoffen, dass Sie etwas über C#, ASP.NET Core und die Visual Studio-IDE gelernt haben. Fahren Sie für weitere Informationen mit dem Tutorial fort.

 > [!div class="nextstepaction"]
 > [Erste Schritte mit ASP.NET Core MVC und Visual Studio](/aspnet/core/tutorials/first-mvc-app/start-mvc?tabs=aspnetcore2x)
