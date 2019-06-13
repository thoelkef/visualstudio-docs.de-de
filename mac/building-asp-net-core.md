---
title: Erstellen von ASP.NET Core-Anwendungen in Visual Studio für Mac
description: In diesem Artikel erfahren Sie mehr über die ersten Schritte mit ASP.NET in Visual Studio für Mac, insbesondere über die Installation und das Erstellen eines neuen Projekts.
author: asb3993
ms.author: amburns
ms.date: 05/30/2019
ms.assetid: 771C2F8E-46BC-4280-AFE8-ED9D5C7790CE
ms.openlocfilehash: fb70966dd24c4d22d473b552297a60ddebdce106
ms.sourcegitcommit: cc5fd59e5dc99181601b7db8b28d7f8a83a36bab
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/11/2019
ms.locfileid: "66836179"
---
# <a name="building-aspnet-core-applications-in-visual-studio-for-mac"></a>Erstellen von ASP.NET Core-Anwendungen in Visual Studio für Mac 


ASP.NET Core ist ein Open Source- und plattformübergreifende-Framework zum Erstellen von modernen cloudbasierten Anwendungen mit Internetverbindung, wie z. B. Web-apps und Diensten, IoT-apps und mobile Back-Ends. ASP.NET Core-apps können auf Ausführen [.NET Core](https://www.microsoft.com/net/core/platform) oder auf die .NET Framework-Laufzeiten. Es wurde entworfen, um als optimiertes Entwicklungsframework für apps bereit, die in der Cloud bereitgestellt werden oder lokal ausgeführt. Es besteht aus modularen Komponenten mit minimalem Aufwand, sodass Sie Flexibilität beim Erstellen Ihrer Lösungen beibehalten. Sie können Ihre ASP.NET Core-Apps plattformübergreifend unter Windows, macOS und Linux ausführen und entwickeln. ASP.NET Core ist auf [GitHub](https://github.com/aspnet/home) verfügbar.

In dieser Übungseinheit erstellen und Untersuchen von ASP.NET Core-Anwendungen mit Visual Studio für Mac.

## <a name="objectives"></a>Ziele


> [!div class="checklist"]
> * Erstellen einer ASP.NET Core-Web-App
> * Untersuchen Sie die ASP.NET Core-hosting, Konfiguration und middlewaremodell
> * Debuggen Sie eine ASP.NET Core-Web-app

## <a name="prerequisites"></a>Erforderliche Komponenten

- [Visual Studio für Mac](https://www.visualstudio.com/vs/visual-studio-mac)

## <a name="intended-audience"></a>Zielgruppe

Diese Übungseinheit richtet sich an Entwickler, die mit vertraut sind C#, obwohl tagtäglich nicht erforderlich ist.

## <a name="task-1-creating-a-new-aspnet-core-application"></a>Aufgabe 1: Erstellen einer neuen ASP.NET Core-Anwendung

1. Starten Sie **Visual Studio für Mac**.

2. Klicken Sie auf **Datei > Neue Projektmappe**.

3. Wählen Sie die **.NET Core > App** Kategorie und die **ASP.NET Core-Web-App (C#)** Vorlage. Klicken Sie auf **Weiter**.

    ![](media/netcore-image1.png)

4. Geben Sie einen Namen **"CoreLab"** , und klicken Sie auf **erstellen** zum Erstellen des Projekts. Es dauert einen Moment Zeit abgeschlossen.

    ![](media/netcore-image2.png)

## <a name="task-2-touring-the-solution"></a>Aufgabe 2: Die Lösung Touring

1. Die Standardvorlage erzeugt eine Lösung mit einem einzelnen ASP.NET Core-Projekt mit dem Namen **CoreLab**. Erweitern Sie den Projektknoten, um seinen Inhalt anzuzeigen.

    ![](media/netcore-image3.png)

2. Dieses Projekt folgt das Model-View-Controller (MVC)-Paradigma zum Bereitstellen einer klaren Trennung der Aufgaben zwischen Daten (Modelle), die Präsentation (Views) und Funktionen (Controller). Öffnen Sie im Ordner **Controller** die Datei **HomeController.cs**.

    ![](media/netcore-image4.png)

3. Die **HomeController** -Klasse durch Konvention-Handles alle eingehenden Anforderungen, die mit beginnen **/Home**. Die **Index** Methode verarbeitet die Anforderungen an den Stamm des Verzeichnisses (z. B. http://site.com/Home) und andere Methoden verarbeiten die Anforderungen an ihre benannten Pfad entsprechend den Konventionen, z. B. **About()** Behandlung von Anforderungen an **http://site.com/Home/About** . Dies ist natürlich alle konfigurierbaren. Eine wichtigste Änderung betrifft, die die **HomeController** ist der Standardcontroller in einem neuen Projekt, in das Stammverzeichnis der Website daher fordert ( **http://site.com** ) durchlaufen würde **Index()** von der **HomeController** wie Anforderungen an **http://site.com/Home** oder **http://site.com/Home/Index** .

    ![](media/netcore-image5.png)

4. Das Projekt hat auch eine **Ansichten** Ordner, der andere Ordner enthält, die den Controllern entsprechen (sowie einen namens **Shared** Ansichten. Die CSHTML-Ansichtsdatei (eine Erweiterung von HTML) des Pfads **/Home/About** wäre z.B. **Views/Home/About.cshtml**. Öffnen Sie diese Datei.

    ![](media/netcore-image6.png)

5. Diese CSHTML-Datei verwendet die Razor-Syntax, um HTML auf der Grundlage einer Kombination von Standardtags und Inline-C# zu rendern. Weitere Informationen finden Sie in der [Onlinedokumentation](https://docs.microsoft.com/aspnet/web-pages/overview/getting-started/introducing-razor-syntax-c).

    ![](media/netcore-image7.png)

6. Die Lösung enthält auch eine **"Wwwroot"** Ordner an, das Stammverzeichnis für Ihre Website kann. Sie können statische Websiteinhalte wie CSS, Bilder und JavaScript-Bibliotheken direkt in den Pfaden einfügen, in denen sie sich bei der Bereitstellung der Website befinden sollen.

    ![](media/netcore-image8.png)

7. Es gibt auch verschiedene Konfigurationsdateien, mit denen Projekte einschließlich der Pakete und die Anwendung zur Laufzeit verwaltet werden können. Die [Standardkonfiguration](https://docs.microsoft.com/aspnet/core/fundamentals/configuration) der Anwendung befindet sich z.B. in der Datei **appsettings.json**. Sie können jedoch einige bzw. alle diese Einstellungen umgebungsabhängig überschreiben, d.h. beispielsweise die Datei **appSettings.Development.json** für die Umgebung **Entwicklung** bereitstellen.

    ![](media/netcore-image9.png)

## <a name="task-3-understanding-how-the-application-is-hosted"></a>Aufgabe 3: Verstehen, wie die Anwendung gehostet wird

1. Von **Projektmappen-Explorer**öffnen **"Program.cs"** . Dies ist die Bootstrapperdatei, die Ihre Anwendung ausgeführt wird.

    ![](media/netcore-image10.png)

2. Es gibt nur zwei Zeilen Code, sind wesentliche. Sie unterteilen wir nach unten. Zunächst wird ein neues **WebHostBuilder** erstellt wird. ASP.NET Core-apps erfordern, einen Host in der ausgeführt wird. Ein Host muss implementieren die **"iwebhost"** -Schnittstelle, die Auflistungen von Funktionen und Dienste zur Verfügung stellt, und ein **starten** Methode. Der Host ist in der Regel erstellt mithilfe einer Instanz von einem **WebHostBuilder**, die erstellt und zurückgibt eine **WebHost** Instanz. Die **WebHost** verweist auf den Server, die Anforderungen behandelt.

    ![](media/netcore-image11.png)

3. Während der **WebHostBuilder** ist verantwortlich für die Erstellung des Hosts, die den Server für die app das Bootstrapping wird, muss Sie angeben, dass einen Server, der implementiert **IServer**. Standardmäßig ist dies  **[Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel)** , ein plattformübergreifenden Webserver für ASP.NET Core basierend auf **Libuv**, dies ist eine plattformübergreifenden asynchronen e/a-Bibliothek.

    ![](media/netcore-image12.png)

4. Als Nächstes wird inhaltsstammverzeichnis des Servers festgelegt. Dadurch wird bestimmt, in denen nach Inhaltsdateien gespeichert, wie MVC-Ansicht-Dateien sucht. Das standardinhaltsstammverzeichnis ist der Ordner, von dem die Anwendung ausgeführt wird.

    ![](media/netcore-image13.png)

5. Wenn die app mit dem Webserver (Internet Information Services, IIS) arbeiten muss die **UseIISIntegration** -Methode aufgerufen werden soll, im Rahmen der Erstellung des Hosts. Dass dies einen Server, nicht wie konfiguriert **"usekestrel"** ist. Um IIS mit ASP.NET Core verwenden zu können, müssen Sie angeben, beide **"usekestrel"** und **UseIISIntegration**. **Kestrel** hinter einem Proxy ausgeführt werden soll, und sollte nicht direkt mit dem Internet bereitgestellt werden. **UseIISIntegration** IIS als Reverseproxyserver zu verwenden, aber sie ist nur relevant, gibt an, wenn auf Computern ausgeführt werden, die IIS verfügen. Wenn Sie Ihre Anwendung in Windows bereitstellen, lassen sie in das. Andernfalls programmieren.

    ![](media/netcore-image14.png)

6. Es ist eine sauberere Methode um das Laden der Einstellungen aus das bootstrapping der Anwendung zu trennen. Ganz einfach dazu **UseStartup** wird aufgerufen, um anzugeben, dass die **Start** Klasse ist für das Laden von Einstellungen und anderen Systemstartaufgaben, z. B. Einfügen von Middleware in der HTTP-Pipeline aufgerufen werden. Sie müssen möglicherweise mehrere **UseStartup** Aufrufe unter der Annahme, dass jeweils vorherige Einstellungen überschreibt, je nach Bedarf.

    ![](media/netcore-image15.png)

7. Der letzte Schritt beim Erstellen der **"iwebhost"** besteht im Aufrufen **erstellen**.

    ![](media/netcore-image16.png)

8. Während **"iwebhost"** Klassen sind erforderlich, um den nicht blockierenden implementieren **starten**, ASP.NET Core-Projekte haben eine Erweiterungsmethode namens **ausführen** , umschließt  **Starten Sie** mit Code blockiert, weshalb Sie nicht manuell verhindern, dass sofort beendet.

    ![](media/netcore-image17.png)

## <a name="task-4-running-and-debugging-the-application"></a>Aufgabe 4: Ausführen und Debuggen der Anwendungs

1. In **Projektmappen-Explorer**, mit der rechten Maustaste die **CoreLab** Projektknoten, und wählen Sie **Optionen**.

    ![](media/netcore-image18.png)

2. Die **Projektoptionen** Dialogfeld enthält alles, was Sie benötigen, um anzupassen, wie die Anwendung erstellt und ausgeführt wird. Wählen Sie die **ausführen > Konfigurationen > Standard** Knoten im linken Bereich.

3. Überprüfen Sie **auf externer Konsole ausführen** , und deaktivieren Sie **Konsolenausgabe anhalten**. Normalerweise den selbst gehostete Anwendung würde nicht die Konsole sichtbar, aber stattdessen die Ergebnisse mit dem protokollieren die **Ausgabe** Pad. Für die Zwecke dieser testumgebung können zeigen sie in einem separaten Fenster, wir, obwohl Sie nicht, die während der normalen Entwicklung werden müssen.

4. Klicken Sie auf **OK**.

    ![](media/netcore-image19.png)

5. Drücken Sie **F5**, um die Anwendung zu erstellen und auszuführen. Alternativ können Sie auswählen **ausführen > Debuggen starten**.

6. Visual Studio für Mac startet zwei Fenster. Die erste ist ein Konsolenfenster, das Ihnen einen Einblick in die Anwendung selbst gehosteten Server bietet.

    ![](media/netcore-image20.png)

7. Die zweite ist ein typisches Browserfenster mit die Website testen. Als der Browser erkennt, kann diese Anwendung an einer beliebigen Stelle gehostet werden. Klicken Sie auf **zu** zu dieser Seite navigieren.

    ![](media/netcore-image21.png)

8. Unter anderem die Infoseite rendert Text im Controller festgelegt.

    ![](media/netcore-image22.png)

9. Lassen Sie beide Fenster öffnen und zurück zu Visual Studio für Mac. Öffnen Sie **Controllers/HomeController.cs**, wenn es nicht bereits geöffnet ist.

    ![](media/netcore-image23.png)

10. Legen Sie in der ersten Zeile der Methode **About** einen Haltepunkt fest. Sie erreichen dies durch Klicken auf den Rand oder Festlegen des Cursors in der Zeile, und drücken **F9**. Diese Zeile legt einige Daten der Auflistung **ViewData** fest, die auf der CSHTML-Seite unter **Views/Home/About.cshtml** gerendert wird.

    ![](media/netcore-image24.png)

11. Zurück zu den Browser, und aktualisieren die Infoseite. Dies löst den Haltepunkt in Visual Studio für Mac.

12. Bewegen Sie den Mauszeiger über die **"ViewData"** Member, um dessen Daten anzuzeigen. Sie können auch seine untergeordneten Elemente, um die geschachtelten Daten finden Sie unter erweitern.

    ![](media/netcore-image25.png)

13. Entfernen Sie den Anwendungshaltepunkt mit derselben Methode, mit der Sie ihn hinzugefügt haben.

14. Öffnen Sie **Views/Home/About.cshtml**.

15. Ändern Sie den Text **additional** in **changed**, und speichern Sie die Datei.

    ![](media/netcore-image26.png)

16. Drücken Sie die **Weiter** Schaltfläche, um die Ausführung fortzusetzen.

    ![](media/netcore-image27.png)

17. Kehren Sie zum Browserfenster zurück, um den aktualisierten Text zu prüfen. Diese Änderung kann zu einem beliebigen Zeitpunkt ausgeführt werden und einen Debughaltepunkt, nicht unbedingt erforderlich ist. Aktualisieren Sie den Browser, wenn die Änderung sofort nicht angezeigt wird.

    ![](media/netcore-image28.png)

18. Schließen Sie Test-Fenster und-Anwendungen Browserkonsole. Dadurch wird die nun auch das Debuggen beendet.

## <a name="task-5-application-startup-configuration"></a>Aufgabe 5: Start-Anwendungskonfiguration

1. Von **Projektmappen-Explorer**öffnen **"Startup.cs"** . Sie können einige roten Wellenlinien anfänglich Beachten Sie, wie NuGet-Pakete im Hintergrund wiederhergestellt werden, und der Roslyn-Compiler ist ein vollständiges Bild von den Abhängigkeiten des Projekts erstellen.

    ![](media/netcore-image29.png)

2. Suchen Sie die **Start** Methode. In diesem Abschnitt wird die anfängliche Konfiguration für die Anwendung definiert und sind dicht gepackt. Näher darauf.

    ![](media/netcore-image30.png)

3. Die Methode beginnt mit der Initialisierung einer **"configurationbuilder"** und Festlegen der Basispfad.

    ![](media/netcore-image31.png)

4. Als Nächstes lädt ein erforderliches **"appSettings.JSON"** Datei.

    ![](media/netcore-image32.png)

5. Versucht, einer umgebungsspezifischen laden **"appSettings.JSON"** -Datei, die vorhandene Einstellungen überschreiben würde. Dies ist z. B. ein bereitgestelltes **"appSettings". Development.JSON** Datei, die für diese bestimmte Umgebung verwendet. Weitere Informationen zur Konfiguration in ASP.NET Core, sehen Sie sich [Dokumentation](https://docs.microsoft.com/aspnet/core/fundamentals/configuration).

    ![](media/netcore-image34.png)

6. Schließlich werden die Umgebungsvariablen an den konfigurationsbuilder hinzugefügt, und die Konfiguration erstellt, und legen Sie für die Nutzung wird.

    ![](media/netcore-image35.png)

## <a name="task-6-inserting-application-middleware"></a>Aufgabe 6: Einfügen von Middleware der Anwendung

1. Suchen Sie die **konfigurieren** -Methode in der die **Start** Klasse. Dies ist, in dem die gesamte Middleware konfiguriert ist, damit es in der HTTP-Pipeline eingefügt und zum Verarbeiten jeder Anforderung an den Server verwendet werden kann. Obwohl diese Methode nur einmal auf den Inhalt der Methoden aufgerufen wird (z. B. **UseStaticFiles**) können für jede Anforderung ausgeführt werden.

    ![](media/netcore-image36.png)

2. Sie können auch zusätzlichen Middleware, die als Teil der Pipeline ausgeführt werden hinzufügen. Fügen Sie den folgenden Code nach dem **app. UseStaticFiles** zum automatischen Hinzufügen einer **X-Test** Header zu jeder ausgehenden Antwort. IntelliSense hilft, den Code zu vervollständigen, während der Eingabe.

    ```csharp
    app.Use(async (context, next) =>
    {
        context.Response.Headers.Add("X-Test", new[] { "Test value" });
        await next();
    });
    ```

3. Drücken Sie **F5**, um das Projekt zu erstellen und auszuführen.

4. Wir können den Browser verwenden, überprüfen Sie die Header, um sicherzustellen, dass sie hinzugefügt werden. Die folgenden Anweisungen sind für Safari, aber Sie können auch erreichen [Chrome](https://stackoverflow.com/questions/4423061/view-http-headers-in-google-chrome) oder [Firefox](https://stackoverflow.com/questions/33974595/in-firefox-how-do-i-see-http-request-headers-where-in-web-console).

5. Wählen Sie nach der der Browser die Website lädt, **Safari > Voreinstellungen**.

6. Auf der **erweitert** Registerkarte **anzeigen Menü in der Menüleiste** und das Dialogfeld zu schließen.

    ![](media/netcore-image37.png)

7. Wählen Sie **entwickeln > Anzeigen von Seitenressourcen**.

8. Aktualisieren Sie das Browserfenster, damit die neu geöffnete Entwicklertools nachverfolgen und den Datenverkehr und die Inhalte analysieren können.

9. Die "localhost" HTML-Seite, die vom Server gerendert werden das Element, das standardmäßig aktiviert.

    ![](media/netcore-image38.png)

10. Erweitern Sie die **Details Randleiste**.

    ![](media/netcore-image39.png)

11. Führen Sie einen Bildlauf zum unteren Rand der Randleiste finden in der Antwort-Header, die zuvor im Code hinzugefügt.

    ![](media/netcore-image40.png)

12. Schließen Sie das Browserfenster, und bei Nichterfüllung-Konsole.

## <a name="summary"></a>Zusammenfassung

In dieser Übungseinheit haben Sie gelernt, wie Sie beginnen, Entwickeln von ASP.NET Core-apps mit Visual Studio für Mac. Wenn Sie möchten, um zu untersuchen, entwickeln eine vollständige Filme-datenbankanwendung, finden Sie unter den [erste Schritte mit ASP.NET Core MVC](https://docs.microsoft.com/aspnet/core/tutorials/first-mvc-app/start-mvc) Tutorial.
