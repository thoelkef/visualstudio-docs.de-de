---
title: 'Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio | Microsoft-Dokumentation'
description: Eine kurze Einführung in die Benutzung von Python in Visual Studio, bei der eine einfache Webanwendung mit dem Falcon-Framework erstellt wird.
ms.custom: ''
ms.date: 03/14/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: ''
ms.topic: quickstart
dev_langs:
- python
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 2b1880d95fcb4aae04d98171c8ee7df7373aaceb
ms.sourcegitcommit: 236c250bb97abdab99d00c6525d106fc0035d7d0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/17/2018
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio erstellen wir eine einfache Python-Webanwendung. Wenn Sie Visual Studio noch nicht installiert haben, gehen Sie auf die Seite [Visual Studio-Downloads](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), um es kostenlos herunterzuladen. Wählen Sie im Installer die Workload **Python-Entwicklung** aus.

## <a name="create-the-project"></a>Erstellen eines Projekts

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie oben in der Menüleiste auf **Datei > Neu > Projekt…**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich den Knoten **Installiert**, und klicken Sie dann auf **Python**.

1. Klicken Sie im mittleren Bereich auf **Webprojekt**, geben Sie dem Projekt einen Namen wie „HelloPython“, und klicken Sie dann auf **OK**.

    ![Dialogfeld „Neues Projekt“ mit der Auswahl „Python-Webprojekt“](media/quickstart-python-00-web-project.png)

    Wenn Ihnen keine Python-Projektvorlagen angezeigt werden, schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie oben in der Menüleiste auf **Extras > Tools und Features abrufen…**, um den Visual Studio-Installer zu öffnen. Klicken Sie beispielsweise auf die Workload **Python-Entwicklung** und anschließend auf **Ändern**.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](../python/media/installation-python-workload.png)

1. Das neue Projekt wird im **Projektmappen-Explorer** im rechten Bereich geöffnet. Zu diesem Zeitpunkt ist das Projekt noch leer und enthält keine anderen Dateien.

    ![Projektmappen-Explorer mit dem neu erstellten leeren Projekt](media/quickstart-python-01-empty-project.png)

**Frage: Welche Vorteile bestehen beim Erstellen eines Projekts für eine Python-Anwendung in Visual Studio?**

Antwort: Python-Anwendungen werden in der Regel nur mit Ordnern und Dateien definiert, diese Struktur kann jedoch bei größeren Anwendungen, die möglicherweise automatisch generierte Dateien, JavaScript für Webanwendungen usw. einbeziehen, komplex werden. Ein Visual Studio-Projekt kann Sie beim Verwalten dieser komplexen Struktur unterstützen. Das Python-Projekt (eine `.pyproj`-Datei) identifiziert alle Quell- und Inhaltsdateien des Projekts, enthält Buildinformationen für jede Datei, verwaltet die Informationen zur Integration in Quellcodeverwaltungssysteme und unterstützt Sie beim Organisieren Ihrer Anwendung in logische Komponenten.

## <a name="install-the-falcon-library"></a>Installieren der Falcon-Bibliothek

Web-Apps in Python verwenden fast immer eine der vielen verfügbaren Python-Bibliotheken, um Details auf unterer Ebene wie das Routing von Webanforderungen und Strukturieren von Antworten zu verarbeiten. Visual Studio stellt hierfür eine Vielzahl von Vorlagen für Web-Apps bereit, die die Frameworks „Bottle“, „Flask“ und „Django“ verwenden.

In diesem Schnellstart wird jedoch die Falcon-Bibliothek verwendet, um ein Paket zu installieren und die Web-App von Grund auf neu zu erstellen. (Visual Studio enthält derzeit keine Falcon-spezifischen Vorlagen.) Führen Sie die folgenden Schritte aus, um Falcon in der globalen Standardumgebung zu installieren.

1. Erweitern Sie den Knoten **Python-Umgebungen** im Projekt, um die entsprechende Standardumgebung aufzurufen.

    ![Projektmappen-Explorer mit der Standardumgebung](media/quickstart-python-02-default-environment.png)

1. Klicken Sie mit der rechten Maustaste auf die Umgebung und dann auf **Python-Paket installieren…**. Dieser Befehl öffnet das Fenster **Python-Umgebungen** in der Registerkarte **Pakete**. Geben Sie „Falcon“ in das Suchfeld ein, und wählen Sie **"pip install falcon" from PyPI** ("pip install falcon" from PyPI) aus. Akzeptieren Sie die Aufforderungen zu Administratorberechtigungen, und beobachten Sie den Fortschritt im Fenster **Ausgabe** in Visual Studio. (Eine Aufforderung zur Erhöhung der Rechte wird angezeigt, wenn der Ordner „Pakete“ für die globale Umgebung sich in einem geschützten Bereich wie `c:\program files` befindet.)

    ![Installieren der Falcon-Bibliothek](media/quickstart-python-03-install-package.png)

1. Nach der Installation wird die Bibliothek in der Umgebung im **Projektmappen-Explorer** angezeigt, d.h., dass Sie sie in Python-Code verwenden können.

    ![Installierte Falcon-Bibliothek](media/quickstart-python-04-package-installed.png)

Weitere Informationen zu Falcon finden Sie unter [falconframework.org](https://falconframework.org/).

Statt Bibliotheken in der globalen Umgebung zu installieren, erstellen Entwickler in der Regel eine „virtuelle Umgebung“, in der Bibliotheken für ein bestimmtes Projekt installiert werden. Viele Python-Projektvorlagen in Visual Studio enthalten eine `requirements.txt`-Datei, in der die Bibliotheken aufgelistet werden, von denen die Vorlage abhängig ist. Falls ein Projekt aus einer dieser Vorlagen erstellt wird, löst dies die Erstellung einer virtuellen Umgebung aus, in die die Bibliotheken installiert werden. Weitere Informationen finden Sie unter [Verwenden von virtuellen Umgebungen](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments).

## <a name="add-a-code-file"></a>Hinzufügen einer Codedatei

Nun können Sie Python-Code einfügen, um eine rudimentäre Web-App zu implementieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Hinzufügen > Neues Element**.

1. Klicken Sie im Dialogfeld, das sich daraufhin öffnet, auf **Leere Python-Datei**, geben Sie dieser den Namen `hello.py`, und klicken Sie auf **Hinzufügen**. Die Datei wird in Visual Studio automatisch in einem Editorfenster geöffnet. (Der Befehl **Hinzufügen > Neues Element…** ist sehr hilfreich, da sich damit ganz einfach verschiedene Dateitypen zu einem Projekt hinzufügen lassen. Diese Elementvorlagen stellen oft nützliche Codebausteine bereit.)

1. Kopieren Sie folgenden Code, und fügen Sie diesen in `hello.py` ein:

    ```python
    import falcon

    # In Falcon, define a class for each resource and define on_* methods
    # where * is any standard HTTP methods in lowercase, such as on_get.

    class HelloResource:
        # In this application, the single HelloResource responds to only GET
        # requests, so it has only an on_get method.

        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to HelloResource. If you add
    # other resources, use api.add_route to define the desired
    # resource locators for them.
    api = falcon.API()
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        # Use Python's built-in WSGI reference implementation to run
        # a web server for the application.
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

1. Nach dem Einfügen dieses Codes zeigt Visual Studio möglicherweise eine Wellenlinie unter `falcon` in der ersten Zeile sowie unter `wsgiref.simple.server` in Zeile 20 an. Diese Indikatoren werden angezeigt, wenn Visual Studio noch dabei ist, die IntelliSense-Datenbank für diese Module zu erstellen.

Weitere Informationen zu Falcon finden Sie im englischsprachigen [Falcon-Schnellstart](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf `hello.py`, und klicken Sie auf **Als Startdatei festlegen**. Der Befehl ermittelt die Codedatei, die in Python bei der Ausführung der App startet.

    ![Festlegen der Startdatei für ein Projekt in Projektmappen-Explorer](media/quickstart-python-05-set-as-startup-file.png)

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt „Hello Python“, und klicken Sie auf **Eigenschaften**. Wählen Sie dann die Registerkarte **Debuggen** aus, und legen Sie die Eigenschaft **Portnummer** auf `8080` fest. So wird sichergestellt, dass Visual Studio einen Browser über `localhost:8080` statt über einen zufälligen Port startet.

1. Klicken Sie auf **Debuggen > Starten ohne Debugging** (STRG+F5), um Änderungen an Dateien zu speichern und die App auszuführen.

1. Ein Befehlsfenster mit der Meldung „Starting web app server“ (Web-App-Server wird gestartet) wird angezeigt. Anschließend sollte sich ein Browserfenster zu `localhost:8080` öffnen, in dem die Meldung „Hello, Python!“ (Hallo, Python!) angezeigt wird. Die GET-Anforderung wird ebenfalls im Befehlsfenster angezeigt.

    Wenn kein Browser automatisch geöffnet wird, starten Sie Ihren bevorzugten Browser, und navigieren Sie zu `localhost:8080`.

    Wenn nur die interaktive Python-Shell im Befehlsfenster angezeigt wird oder das Fenster kurz auf dem Bildschirm aufblinkt, sollten Sie überprüfen, ob Sie in Schritt 1 `hello.py` als Startdatei festgelegt haben.

1. Schließen Sie das Befehlsfenster, um die App zu beenden, und schließen Sie dann das Browserfenster.

## <a name="next-steps"></a>Nächste Schritte

Herzlichen Glückwunsch! Sie haben diesen Schnellstart abgeschlossen und die Visual Studio-IDE besser kennengelernt. Wenn Sie ein umfangreicheres Tutorial zu Python in Visual Studio starten möchten, in dem auch die Verwendung des interaktiven Fensters, das Debuggen, die Datenvisualisierung und die Arbeit mit Git behandelt wird, klicken Sie auf die Schaltfläche unten.

> [!div class="nextstepaction"]
> [Tutorial: Erste Schritte mit Python in Visual Studio](../python/tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

- Weitere Informationen zu [Python-Web-App-Vorlagen in Visual Studio](../python/python-web-application-project-templates.md)
- Weitere Informationen zum [Debuggen in Python](../python/debugging-python-in-visual-studio.md)
- Weitere Informationen zur [Visual Studio-IDE](../ide/visual-studio-ide.md)
