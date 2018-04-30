---
title: 'Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio'
description: In diesem Schnellstart verwenden Sie Visual Studio, um mithilfe des Flask-Frameworks eine einfache Web-App in Python zu erstellen.
ms.custom: mvc
ms.date: 03/21/2018
ms.technology:
- vs-acquisition
ms.topic: quickstart
dev_langs:
- python
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: b3a455dc04693b70c0ae3932503aea33085b2a80
ms.sourcegitcommit: 4c0bc21d2ce2d8e6c9d3b149a7d95f0b4d5b3f85
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/20/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio

In dieser fünf- bis zehnminütigen Einführung in Visual Studio als Python-IDE erstellen Sie eine einfache Python-Webanwendung, die auf dem Flask-Framework basiert. Sie erstellen das Projekt über einzelne Schritte, in denen Sie mehr über die grundlegenden Features von Visual Studio erfahren.

Wenn Sie Visual Studio noch nicht installiert haben, können Sie es unter [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs) kostenlos herunterladen. Wählen Sie im Installer die Workload **Python-Entwicklung** aus.

## <a name="create-the-project"></a>Erstellen eines Projekts

In den folgenden Schritten wird ein leeres *Projekt* erstellt, das als Container für die Anwendung fungiert:

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie oben in der Menüleiste auf **Datei > Neu > Projekt…**.

1. Geben Sie im Dialogfeld **Neues Projekt** „Python-Webprojekt“ in das Suchfeld im oberen rechten Bereich ein, wählen Sie **Webprojekt** aus der mittleren Liste aus, geben Sie dem Projekt einen Namen wie „HelloPython“ (HalloPython), und klicken Sie dann auf **OK**.

    ![Dialogfeld „Neues Projekt“ mit der Auswahl „Python-Webprojekt“](media/quickstart-python-00-web-project.png)

    Wenn Ihnen keine Python-Projektvorlagen angezeigt werden, schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie oben in der Menüleiste auf **Extras > Tools und Features abrufen…**, um den Visual Studio-Installer zu öffnen. Klicken Sie beispielsweise auf die Workload **Python-Entwicklung** und anschließend auf **Ändern**.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](../python/media/installation-python-workload.png)

1. Das neue Projekt wird im **Projektmappen-Explorer** im rechten Bereich geöffnet. Zu diesem Zeitpunkt ist das Projekt noch leer und enthält keine anderen Dateien.

    ![Projektmappen-Explorer mit dem neu erstellten leeren Projekt](media/quickstart-python-01-empty-project.png)

**Frage: Welche Vorteile bestehen beim Erstellen eines Projekts für eine Python-Anwendung in Visual Studio?**

**Antwort:** Python-Anwendungen werden in der Regel nur mit Ordnern und Dateien definiert. Diese Struktur kann jedoch bei größeren Anwendungen, die möglicherweise automatisch generierte Dateien, JavaScript für Webanwendungen usw. einbeziehen, komplex werden. Ein Visual Studio-Projekt kann Sie beim Verwalten dieser komplexen Struktur unterstützen. Das Python-Projekt (eine `.pyproj`-Datei) identifiziert alle Quell- und Inhaltsdateien des Projekts, enthält Buildinformationen für jede Datei, verwaltet die Informationen zur Integration in Quellcodeverwaltungssysteme und unterstützt Sie beim Organisieren Ihrer Anwendung in logische Komponenten.

**Frage: Welche Funktion haben die im Projektmappen-Explorer angezeigten „Projektmappen“?**

**Antwort:** Eine *Visual Studio-Projektmappe* ist ein Container, der Ihnen das Verwalten von einem oder mehreren in Zusammenhang stehenden Projekten als Gruppe ermöglicht, und Konfigurationseinstellungen speichert, die nicht für ein Projekt spezifisch sind. Die Projekte in einer Projektmappe können ebenfalls aufeinander verweisen. Dadurch kann das Ausführen eines Projekts (z.B. eine Python-App) beispielsweise automatisch zum Erstellen eines anderen Projekts (z.B. eine C++-Erweiterung, die in der Python-App verwendet wird) führen.

## <a name="install-the-flask-library"></a>Installieren der Flask-Bibliothek

Web-Apps in Python verwenden fast immer eine der vielen verfügbaren Python-Bibliotheken, um Details auf unterer Ebene wie das Routing von Webanforderungen und Strukturieren von Antworten zu verarbeiten. Visual Studio stellt hierfür eine Vielzahl von *Vorlagen* für Web-Apps bereit, von denen Sie eine im Verlauf dieses Schnellstarts verwenden werden.

Hier verwenden Sie folgende Schritte, um die Flask-Bibliothek in der „globalen Umgebung“ (Standardeinstellung) zu installieren, die Visual Studio für dieses Projekt verwendet.

1. Erweitern Sie den Knoten **Python-Umgebungen** im Projekt, um die entsprechende Standardumgebung aufzurufen.

    ![Projektmappen-Explorer mit der Standardumgebung](media/quickstart-python-02-default-environment.png)

1. Klicken Sie mit der rechten Maustaste auf die Umgebung und dann auf **Python-Paket installieren…**. Dieser Befehl öffnet das Fenster **Python-Umgebungen** in der Registerkarte **Pakete**.

1. Geben Sie „Flask“ in das Suchfeld ein, und wählen Sie **pip install flask from PyPI** aus. Akzeptieren Sie die Aufforderungen zu Administratorberechtigungen, und beobachten Sie den Fortschritt im Fenster **Ausgabe** in Visual Studio. (Eine Aufforderung zur Erhöhung der Rechte wird angezeigt, wenn der Ordner „Pakete“ für die globale Umgebung sich in einem geschützten Bereich wie `c:\program files` befindet.)

    ![Installieren der Flask-Bibliothek](media/quickstart-python-03-install-package.png)

1. Nach der Installation wird die Bibliothek in der Umgebung im **Projektmappen-Explorer** angezeigt, d.h., dass Sie sie in Python-Code verwenden können.

    ![Installierte Flask-Bibliothek](media/quickstart-python-04-package-installed.png)

> [!Note]
> Statt Bibliotheken in der globalen Umgebung zu installieren, erstellen Entwickler in der Regel eine „virtuelle Umgebung“, in der Bibliotheken für ein bestimmtes Projekt installiert werden. Visual Studio-Vorlagen stellen diese Option in der Regel bereit. Dies wird unter [Schnellstart: Erstellen eines Python-Projekts mithilfe einer Vorlage](../python/quickstart-02-python-in-visual-studio-project-from-template.md) erläutert.

**Frage: Wo erfahre ich mehr über andere verfügbare Python-Pakete?**

**Antwort:** Besuchen Sie die Seite [Python Package Index](https://pypi.org/) (pypi.org).

## <a name="add-a-code-file"></a>Hinzufügen einer Codedatei

Nun können Sie Python-Code einfügen, um eine rudimentäre Web-App zu implementieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Hinzufügen > Neues Element**.

1. Klicken Sie im Dialogfeld, das sich daraufhin öffnet, auf **Leere Python-Datei**, geben Sie dieser den Namen `app.py`, und klicken Sie auf **Hinzufügen**. Die Datei wird in Visual Studio automatisch in einem Editorfenster geöffnet.

1. Kopieren Sie folgenden Code, und fügen Sie diesen in `app.py` ein:

    ```python
    from flask import Flask

    # Create an instance of the Flask class that is the WSGI application.
    # The first argument is the name of the application module or package,
    # typically __name__ when using a single module.
    app = Flask(__name__)

    # Flask route decorators map / and /hello to the hello function.
    # To add other resources, create functions that generate the page contents
    # and add decorators to define the appropriate resource locators for them.

    @app.route('/')
    @app.route('/hello')
    def hello():
        # Render the page
        return "Hello Python!"

    if __name__ == '__main__':
        # Run the app server on localhost:4449
        app.run('localhost', 4449)
    ```

1. Sie werden feststellen, dass das Dialogfeld **Hinzufügen > Neues Element...** viele weitere Dateitypen enthält, die Sie zu einem Python-Projekt hinzufügen können, zu denen unter anderem eine Python-Klasse, ein Python-Paket, ein Python-Komponententest und web.config-Dateien zählen. Im Allgemeinen sind diese sogenannten *Elementvorlagen* eine gute Möglichkeit, um schnell Dateien mit nützlichen Codebausteinen zu erstellen.

**Frage: Wo erfahre ich mehr über Flask?**

**Antwort:** Lesen Sie die Flask-Dokumentation. Beginnen Sie dabei mit dem [Quickstart (Schnellstart)](http://flask.pocoo.org/docs/0.12/quickstart/#quickstart) (flask.pocoo.org).

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf `app.py`, und klicken Sie auf **Als Startdatei festlegen**. Dieser Befehl ermittelt die Codedatei, die in Python bei der Ausführung der App startet.

    ![Festlegen der Startdatei für ein Projekt in Projektmappen-Explorer](media/quickstart-python-05-set-as-startup-file.png)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und wählen Sie **Eigenschaften** aus. Wählen Sie dann die Registerkarte **Debuggen** aus, und legen Sie die Eigenschaft **Portnummer** auf `4449` fest. Dadurch wird sichergestellt, dass Visual Studio entsprechend der `app.run`-Argumente im Code einen Browser mit `localhost:4449` ausführt.

1. Klicken Sie auf **Debuggen > Starten ohne Debugging** (STRG+F5). Dadurch werden Änderungen an Dateien gespeichert, und die App wird ausgeführt.

1. Ein Befehlsfenster mit der Meldung „* Running in https://localhost:4449/“ (* wird unter https://localhost:4449/ ausgeführt) wird angezeigt, und ein Browserfenster zu `localhost:4449` sollte geöffnet werden, in dem die Meldung „Hello, Python!“ (Hallo, Python!) angezeigt wird. Die GET-Anforderung wird ebenfalls mit dem Status „200“ im Befehlsfenster angezeigt.

    Wenn kein Browser automatisch geöffnet wird, starten Sie Ihren bevorzugten Browser, und navigieren Sie zu `localhost:4449`.

    Wenn nur die interaktive Python-Shell im Befehlsfenster angezeigt wird oder das Fenster kurz auf dem Bildschirm aufblinkt, sollten Sie überprüfen, ob Sie in Schritt 1 `app.py` als Startdatei festgelegt haben.

1. Navigieren Sie zu `localhost:4449/hello`, um zu testen, dass der Decorator der `/hello`-Ressource ebenfalls funktioniert. Die GET-Anforderung wird erneut mit dem Status „200“ im Befehlsfenster angezeigt. Sie sollten ebenfalls andere URLs ausprobieren, um festzustellen, dass diese den Statuscode „404“ im Befehlsfenster anzeigen.

1. Schließen Sie das Befehlsfenster, um die App zu beenden, und schließen Sie dann das Browserfenster.

**Frage: Was ist der Unterschied zwischen den Befehlen „Starten ohne Debugging“ und „Debugging starten“?**

**Antwort:** Sie verwenden **Debugging starten**, um die App mit dem [Visual Studio-Debugger](../python/debugging-python-in-visual-studio.md) zu starten. Dadurch können Sie Breakpoints setzen, Variablen untersuchen und Ihren Code Zeile für Zeile durchlaufen. Apps werden im Debugger aufgrund der zahlreichen Hooks, die das Debuggen ermöglichen, möglicherweise langsamer ausgeführt. Im Gegensatz dazu wird die App durch **Starten ohne Debugging** ohne Debugging direkt so ausgeführt, als würden Sie diese über die Befehlszeile ausführen. Außerdem wird ein Browser gestartet, der zu der URL navigiert, die in der Registerkarte **Debuggen** in den Projekteigenschaften angegeben wurde.

## <a name="next-steps"></a>Nächste Schritte

Glückwunsch zum Ausführen Ihrer ersten Python-App über Visual Studio! Dabei haben Sie mehr über das Verwenden von Visual Studio als Python-IDE erfahren.

Da die Schritte, die Sie in diesem Schnellstart befolgt haben, relativ allgemein sind, können und sollten diese automatisiert werden. Für diese Automatisierung sind die *Visual Studio-Projektvorlagen* vorhanden. Klicken Sie auf die unten stehende Schaltfläche. Dort wird veranschaulicht, wie eine Web-App erstellt in weniger Schritten erstellt wird, die der ähnelt, die Sie gerade erstellt haben.

> [!div class="nextstepaction"]
> [Schnellstart: Erstellen eines Python-Projekts mithilfe einer Vorlage](../python/quickstart-02-python-in-visual-studio-project-from-template.md)

Wenn Sie ein umfangreicheres Tutorial zu Python in Visual Studio starten möchten, in dem auch die Verwendung des interaktiven Fensters, das Debuggen, die Datenvisualisierung und die Arbeit mit Git behandelt wird, klicken Sie auf die Schaltfläche unten.

> [!div class="nextstepaction"]
> [Tutorial: Erste Schritte mit Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

Klicken Sie für weitere Informationen zu den Features von Visual Studio auf folgende Links.

- Weitere Informationen zu [Python-Web-App-Vorlagen in Visual Studio](../python/python-web-application-project-templates.md)
- Weitere Informationen zum [Debuggen in Python](../python/debugging-python-in-visual-studio.md)
- Weitere allgemeine Informationen zur [Visual Studio-IDE](../ide/visual-studio-ide.md)
