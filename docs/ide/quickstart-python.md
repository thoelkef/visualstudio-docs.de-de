---
title: 'Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio | Microsoft-Dokumentation'
ms.custom: 
ms.date: 12/1/2017"
ms.reviewer: 
ms.suite: 
ms.technology: vs-acquisition
ms.tgt_pltfrm: 
ms.topic: quickstart
ms.devlang: python
author: kraigb
ms.author: kraigb
manager: ghogen
dev_langs: python
ms.workload: python
ms.openlocfilehash: bf0a6e187a98a03d3beed33537fe5244ecd5d35d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-use-visual-studio-to-create-your-first-python-web-app"></a>Schnellstart: Erstellen einer ersten Python-Web-App mit Visual Studio

In dieser fünf- bis zehnminütigen Einführung in die integrierte Entwicklungsumgebung (IDE) von Visual Studio erstellen wir eine einfache Python-Webanwendung. Falls Sie Visual Studio noch nicht installiert haben, können Sie es [hier](http://www.visualstudio.com) gratis herunterladen.

## <a name="create-the-project"></a>Erstellen eines Projekts

1. Öffnen Sie Visual Studio 2017.

1. Klicken Sie oben in der Menüleiste auf **Datei > Neu > Projekt…**.

1. Erweitern Sie im Dialogfeld **Neues Projekt** im linken Bereich den Knoten **Andere Projekttypen**, und klicken Sie dann auf **Python**. Klicken Sie im mittleren Bereich auf **Webprojekt**, geben Sie dem Projekt einen Namen wie „HelloPython“, und klicken Sie dann auf **OK**.

    Wenn Ihnen keine Python-Projektvorlagen angezeigt werden, schließen Sie das Dialogfeld **Neues Projekt**, und klicken Sie oben in der Menüleiste auf **Extras > Tools und Features abrufen…**, um den Visual Studio-Installer zu öffnen. Klicken Sie beispielsweise auf die Workload **Python-Entwicklung** und anschließend auf **Ändern**.

    ![Arbeitsauslastung zur Python-Entwicklung im Visual Studio-Installationsprogramm](../python/media/installation-python-workload.png)

1. Das neue Projekt wird im **Projektmappen-Explorer** im rechten Bereich geöffnet. Zu diesem Zeitpunkt ist das Projekt noch leer und enthält keine anderen Dateien.

    ![Projektmappen-Explorer mit dem neu erstellten leeren Projekt](media/quickstart-python-01-empty-project.png)

## <a name="install-the-falcon-library"></a>Installieren der Falcon-Bibliothek

Web-Apps in Python verwenden fast immer eine der vielen verfügbaren Python-Bibliotheken, um Details auf unterer Ebene wie das Routing von Webanforderungen und Strukturieren von Antworten zu verarbeiten. Die Workload „Python-Entwicklung“ in Visual Studio stellt [eine Vielzahl von Vorlagen für Web-Apps](../python/template-web.md) bereit, die auf Bottle-, Flask- und Django-Bibliotheken aufbauen.

In diesem Schnellstart verwenden wir jedoch eine andere Bibliothek, und zwar [Falcon](https://falconframework.org/), um ein Paket zu installieren und die Web-App von Grund auf neu zu erstellen. Führen Sie die folgenden Schritte aus, um Falcon in der globalen Standardumgebung zu installieren.

1. Erweitern Sie den Knoten **Python-Umgebungen** im Projekt, um die entsprechende Standardumgebung aufzurufen.

    ![Projektmappen-Explorer mit der Standardumgebung](media/quickstart-python-02-default-environment.png)

1. Klicken Sie mit der rechten Maustaste auf die Umgebung und dann auf **Python-Paket installieren…**. Dieser Befehl öffnet das Fenster **Python-Umgebungen** in der Registerkarte **Pakete**. Geben Sie „Falcon“ in das Suchfeld ein, und wählen Sie **"pip install falcon" from PyPI** ("pip install falcon" from PyPI) aus. Akzeptieren Sie die Aufforderungen zu Administratorberechtigungen, und beobachten Sie den Fortschritt im Fenster **Ausgabe** in Visual Studio.

    ![Installieren der Falcon-Bibliothek](media/quickstart-python-03-install-package.png)

1. Nach der Installation wird die Bibliothek in der Umgebung im **Projektmappen-Explorer** angezeigt, d.h., dass Sie sie in Python-Code verwenden können.

    ![Installierte Falcon-Bibliothek](media/quickstart-python-04-package-installed.png)

Statt Bibliotheken in der globalen Umgebung zu installieren, erstellen Entwickler in der Regel eine „virtuelle Umgebung“, in der Bibliotheken für ein bestimmtes Projekt installiert werden. Viele Python-Projektvorlagen in Visual Studio enthalten eine `requirements.txt`-Datei, in der die Bibliotheken aufgelistet werden, von denen die Vorlage abhängig ist. Falls ein Projekt aus einer dieser Vorlagen erstellt wird, löst dies die Erstellung einer virtuellen Umgebung aus, in die die Bibliotheken installiert werden. Weitere Informationen finden Sie unter [Virtuelle Umgebungen](../python/python-environments.md#virtual-environments) im Artikel „Python-Umgebungen“.

## <a name="add-a-code-file"></a>Hinzufügen einer Codedatei

Nun können Sie Python-Code einfügen, um eine rudimentäre Web-App zu implementieren.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt, und klicken Sie auf **Hinzufügen > Neues Element**. Wählen Sie im Dialogfeld, das sich daraufhin öffnet, **Leere Python-Datei** aus, nennen Sie sie `hello.py`, und klicken Sie auf **OK**. Die Datei wird in Visual Studio automatisch in einem Editorfenster geöffnet. (Der Befehl **Hinzufügen > Neues Element…** ist sehr hilfreich, da sich damit ganz einfach verschiedene Dateitypen zu einem Projekt hinzufügen lassen. Diese Elementvorlagen stellen oft nützliche Codebausteine bereit.)

1. Kopieren Sie den folgenden Code, und fügen Sie ihn ein, oder geben Sie ihn in `hello.py` ein:

    ```python
    import falcon
    api = falcon.API()

    # In Falcon, define a class for each resource; the on_get 
    # method then handles any GET requests.

    class HelloResource:
        def on_get(self, req, resp):
            resp.status = falcon.HTTP_200  # 200 is the default
            resp.body = "Hello, Python!"

    # Resources are represented by long-lived class instances
    hello = HelloResource()

    # Instruct Falcon to route / and /hello to the HelloResource
    api.add_route('/', hello)
    api.add_route('/hello', hello)

    if __name__ == "__main__":
        from wsgiref.simple_server import make_server

        # Run the web server on localhost:8080
        print("Starting web app server")
        srv = make_server('localhost', 8080, api)
        srv.serve_forever()
    ```

Weitere Informationen zu Falcon finden Sie im englischsprachigen [Falcon-Schnellstart](https://falcon.readthedocs.io/en/stable/user/quickstart.html) (falcon.readthedocs.io).

## <a name="run-the-application"></a>Ausführen der Anwendung

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf `hello.py`, und klicken Sie auf **Als Startdatei festlegen**. Der Befehl ermittelt die Codedatei, die in Python bei der Ausführung der App startet.

1. Klicken Sie im **Projektmappen-Explorer** mit der rechten Maustaste auf das Projekt „Hello Python“, und klicken Sie auf **Eigenschaften**. Wählen Sie dann die Registerkarte **Debuggen** aus, und legen Sie die Eigenschaft **Portnummer** auf `8080` fest. So wird sichergestellt, dass Visual Studio einen Browser über `localhost:8080` statt über einen zufälligen Port startet.

1. Klicken Sie auf **Debuggen > Starten ohne Debugging** (STRG+F5), um Änderungen an Dateien zu speichern und die App auszuführen.

1. Ein Befehlsfenster mit der Meldung „Starting web app server“ (Web-App-Server wird gestartet) wird angezeigt. Anschließend öffnet sich ein Browserfenster zu `localhost:8080`, in dem die Meldung „Hello, Python!“ angezeigt wird. Die GET-Anforderung wird ebenfalls im Befehlsfenster angezeigt. (Wenn nur die interaktive Python-Shell im Befehlsfenster angezeigt wird oder das Fenster kurz auf dem Bildschirm aufblinkt, sollten Sie überprüfen, ob Sie in Schritt 1 oben `hello.py` als Startdatei festgelegt haben.)

1. Schließen Sie das Befehlsfenster, um die App zu beenden.

## <a name="next-steps"></a>Nächste Schritte

Herzlichen Glückwunsch! Sie haben diesen Schnellstart abgeschlossen und die Visual Studio-IDE etwas besser kennengelernt. Wenn Sie ein umfangreicheres Tutorial zu Python in Visual Studio starten möchten, in dem auch die Verwendung des interaktiven Fensters, das Debuggen, die Datenvisualisierung und die Arbeit mit Git behandelt wird, klicken Sie auf die Schaltfläche unten.

> [!div class="nextstepaction"]
> [Tutorial: Erste Schritte mit Python in Visual Studio](../python/vs-tutorial-01-01.md)

- Weitere Informationen zu [Python-Web-App-Vorlagen in Visual Studio](../python/template-web.md)
- Weitere Informationen zur [Visual Studio-IDE](../ide/visual-studio-ide.md)
- Weitere Informationen zur Verwendung des [Visual Studio-Debuggers](../debugger/debugger-feature-tour.md)