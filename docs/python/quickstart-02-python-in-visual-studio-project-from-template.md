---
title: 'Schnellstart: Erstellen eines Python-Projekts mithilfe einer Vorlage'
description: In diesem Schnellstart erstellen Sie ein Visual Studio-Projekt für Python mithilfe der integrierten Vorlage für eine einfache Flask-App.
ms.date: 05/07/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: quickstart
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: dca1e37a0cde89a2a531d3fceea4337bb9e348dd
ms.sourcegitcommit: 4c0db930d9d5d8b857d3baf2530ae89823799612
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2018
ms.locfileid: "33957336"
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage in Visual Studio

Wenn Sie die [Python-Unterstützung in Visual Studio 2017 installiert haben](installing-python-support-in-visual-studio.md), können Sie ganz einfach ein neues Python-Projekt mithilfe einer Vielzahl von Vorlagen erstellen. In diesem Schnellstart erstellen Sie eine einfache Flask-Anwendung mit einer Vorlage. Das entstehende Projekt ist so ähnlich wie das Projekt, dass Sie unter [Schnellstart: Erstellen einer Web-App mit Flask](../ide/quickstart-python.md) erstellt haben.

1. Starten Sie Visual Studio 2017.

1. Klicken Sie oben in der Menüleiste auf **Datei > Neu > Projekt...**, suchen Sie anschließend im Dialogfeld **Neues Projekt** nach „leeres flask“, wählen Sie dann die Vorlage „Leeres Flask-Webprojekt“ aus der mittleren Liste aus, benennen Sie das Projekt, und klicken Sie dann auf **OK**:

    ![Erstellen eines neuen Projekts mit der Vorlage „Leeres Flask-Webprojekt“](media/quickstart-python-06-blank-flask-template.png)

1. Visual Studio zeigt die folgende Aufforderung an: „This project requires external packages.“ (Für dieses Projekt sind externe Pakete erforderlich.). Dieses Dialogfeld wird angezeigt, weil die Vorlage eine `requirements.txt`-Datei enthält, die eine Abhängigkeit zu Flask enthält. Visual Studio kann das Paket automatisch installieren. Sie erhalten die Option, sie als *virtuelle Umgebungen* zu installieren. Das Verwenden einer virtuellen Umgebung ist der Installation in einer globalen Umgebung vorzuziehen. Wählen Sie deshalb **Install into a virtual environment** (In einer virtuellen Umgebung installieren), um fortzufahren.

    ![Flask in einer virtuellen Umgebung installieren](media/quickstart-python-07-install-into-virtual-environment.png)

1. Visual Studio zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** an. Übernehmen Sie die Standardeinstellungen, und klicken Sie auf **Erstellen**. Stimmen Sie etwaigen Anforderungen von Rechteerweiterungen zu.

    > [!Tip]
    > Wenn Sie mit einem neuen Projekt beginnen, wird dringend empfohlen, zu Beginn eine virtuelle Umgebung zu erstellen. Dazu werden Sie auch von den meisten Visual Studio-Vorlagen aufgefordert. Virtuelle Umgebungen behalten die genauen Anforderungen Ihres Projekts im Laufe der Zeit bei, wenn Bibliotheken hinzugefügt und entfernt werden. Dann können Sie mühelos eine `requirements.txt`-Datei erstellen, die Sie zur erneuten Installation dieser Abhängigkeiten auf anderen Entwicklungscomputern verwenden können (wie bei der Quellcodeverwaltung). Außerdem können Sie diese Datei verwenden, wenn Sie das Projekt auf einem Produktionsserver bereitstellen. Weitere Informationen zu virtuellen Umgebungen und deren Vorzügen finden Sie in den Artikeln [Auswählen eines Python-Interpreters und einer Umgebung zur Verwendung in einem Projekt](../python/selecting-a-python-environment-for-a-project.md#using-virtual-environments) und [Verwalten von erforderlichen Paketen mit „requirements.txt“](../python/managing-required-packages-with-requirements-txt.md).

1. Nachdem Visual Studio diese Umgebung erstellt hat, sehen Sie im **Projektmappen-Explorer** neben `requirements.txt` auch eine `app.py`-Datei. Öffnen Sie `app.py`. Dann sehen Sie, dass die Vorlage Code bereitgestellt hat, der dem unter [Schnellstart: Erstellen einer Web-App mit Flask](../ide/quickstart-python.md) ähnelt, mit zwei zusätzlichen Bereichen.

    Oben sehen Sie die Zeile `wsgi_app = app.wsgi_app`, die beim Bereitstellen einer App für einen Webhost nützlich sein kann.

    Darunter sehen Sie den Startcode, mit dem Sie den Host und Port anhand von Umgebungsvariablen festlegen können statt sie zu hartcodieren. Mit derartigem Code können Sie die Konfiguration auf Entwicklungs- und Produktionscomputern steuern, ohne den Code ändern zu müssen:

    ```python
    if __name__ == '__main__':
        import os
        HOST = os.environ.get('SERVER_HOST', 'localhost')
        try:
            PORT = int(os.environ.get('SERVER_PORT', '5555'))
        except ValueError:
            PORT = 5555
        app.run(HOST, PORT)
    ```

1. Klicken Sie auf **Debuggen > Ohne Debuggen starten**, um das Programm auszuführen und `localhost:5555` in einem Browser zu öffnen.

**Frage: Welche anderen Python-Vorlagen werden von Visual Studio bereitgestellt?**

**Antwort:** Wenn die Python-Workload installiert ist, stellt Visual Studio verschiedenste Projektvorlagen bereit, darunter Vorlagen für [die Webframeworks Flask, Bottle und Django](../python/python-web-application-project-templates.md), für Azure-Clouddienste, unterschiedliche Machine Learning-Szenarios und sogar eine Vorlage zum Erstellen eines Projekts mit einer bereits vorhandenen Ordnerstruktur, die eine Python-App enthält. Auf diese Vorlagen können Sie über **Datei > Neu > Projekt** zugreifen. Klicken Sie dafür auf den Knoten für **Python**, und wählen Sie untergeordnete Knoten aus.

Visual Studio bietet auch unterschiedliche *Datei- und Elementvorlagen* zum schnellen Erstellen einer Python-Klasse, eines Python-Pakets, eines Python-Komponententest, von `web.config`-Dateien usw. Wenn Sie ein Python-Projekt geöffnet haben, können Sie über den Menübefehl **Projekt > Neues Element hinzufügen...** auf Elementvorlagen zugreifen. Weitere Informationen finden Sie in der [Referenz für Python-Elementvorlagen](python-item-templates.md).

Durch das Verwenden von Vorlagen sparen Sie deutlich Zeit, wenn Sie mit einem Projekt beginnen oder eine Datei erstellen. Zudem können Sie durch Vorlagen neue App-Typen und Codestrukturen kennenlernen. Es kann von Vorteil sein, sich etwas Zeit zu nehmen und Projekte und Elemente mit verschiedenen Vorlagen zu erstellen. So können Sie sich mit den zur Verfügung stehenden Vorlagen vertraut machen.

**Frage: Kann ich auch Cookiecutter-Vorlagen verwenden?**

**Antwort:** Ja. Cookiecutter-Vorlagen sind sogar direkt in Visual Studio integriert. Informationen dazu finden Sie unter [Quickstart: create a project from a Cookiecutter template (Schnellstart: Erstellen eines Projekts mit einer Cookiecutter-Vorlage)](../python/quickstart-04-python-in-visual-studio-project-from-cookiecutter.md).

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](tutorial-working-with-python-in-visual-studio-step-01-create-project.md)

## <a name="see-also"></a>Siehe auch

- [Manuelles Identifizieren eines vorhandenen Python-Interpreters](managing-python-environments-in-visual-studio.md#manually-identify-an-existing-environment)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installing-python-support-in-visual-studio.md)
- [Installationsspeicherorte](installing-python-support-in-visual-studio.md#install-locations)
