---
ms.topic: include
ms.openlocfilehash: b629de8144e08c7c0019a0a116f84e5877c3a477
ms.sourcegitcommit: 928885ace538bef5b25961358d4f166d648f196a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2018
---
### <a name="create-a-project-using-django-20"></a>Erstellen eines Projekts mit Django 2.0

Die leere Django-Webprojektvorlage verwendet derzeit die neueste Version Django 1.x. Die schnellste Möglichkeit zur Verwendung von Django 2.x ist der Import von Django 2.x-Dateien in ein Django 1.x-Projekt. Wenn Sie diesen Prozess befolgen, nutzen Sie weitere Details, die von der Visual Studio-Projektvorlage genutzt werden.

1. Erstellen Sie ein Django 1.x-Projekt mithilfe der Vorlage „Leeres Django-Webprojekt“, wie im vorherigen Abschnitt beschrieben. Wählen Sie jedoch in der Eingabeaufforderung „This project requires external dependencies“ (Dieses Projekt erfordert externe Abhängigkeiten) **Ich führe die Installation selbst durch** aus. Sie wählen diese Option, um das Installieren von Abhängigkeiten zu vermeiden, die in einem späteren Schritt deinstalliert werden.

1. Öffnen Sie eine Eingabeaufforderung, und navigieren Sie zu einem temporären Ordner.

1. Führen Sie `pip install django` aus, um das aktuellste Django-Paket in Ihrer globalen Python-Umgebung zu installieren.

1. Führen Sie `django-admin startproject <project_name>` aus, ersetzen sie `<project_name>` mit dem gleichen Projektnamen aus Schritt 1, z.B. „HelloDjango“. Der `startproject`-Befehl erstellt eine `manage.py`-Datei sowie einen Ordner, der mit `<project_name>` übereinstimmt, der die Dateien `__init.py__`, `settings.py`, `urls.py` und `wsgi.py` enthält.

1. Ersetzen Sie in Visual Studio wie folgt die Django 1.x-Dateien im Projekt durch die Django 2.x-Dateien:

  a. Löschen Sie im **Projektmappen-Explorer** `manage.py` und den Django-App-Ordner.
  b. Klicken Sie mit der rechten Maustaste auf das Projekt, wählen Sie den Befehl **Hinzufügen > Vorhandenes Element...**  aus, navigieren Sie zu der im Schritt 4 erstellten `manage.py`-Datei, wählen diese aus, und klicken Sie auf **OK**. Visual Studio kopiert die Datei dann in das Projekt.
  c. Klicken Sie mit der rechten Maustaste erneut auf das Projekt, wählen Sie den Befehl **Hinzufügen > Vorhandener Ordner...**  aus, navigieren Sie zu dem in Schritt 4 erstellten App-Ordner, wählen Sie diesen aus, und klicken Sie auf **OK**. Visual Studio kopiert dann den gesamten Ordner und seine vier Dateien in das Projekt.
  d. Klicken Sie mit der rechten Maustaste auf `manage.py`, und klicken Sie auf **Als Startdatei festlegen**.

  > [!Important]
  > Der Name der App im Visual Studio-Projekt muss mit `<project_name>` übereinstimmen. Dies wird im `django-admin`-Hilfsprogramm verwendet, weil das Hilfsprogramm diesen Namen als Namespace in den Python-Codedateien verwendet.

1. Öffnen Sie `requirements.txt`, ändern Sie den Inhalt in `django >=2.0, <3`, und speichern Sie die Datei.

1. Klicken Sie mit der rechten Maustaste im **Projektmappen-Explorer** auf den Knoten **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen...** aus. Akzeptieren Sie die Standardeinstellungen im angezeigten Dialogfeld, und wählen Sie **Erstellen** aus. Akzeptieren Sie die Aufforderungen für Administratorrechte.