---
title: Auswählen eines Python-Interpreters und einer Umgebung für ein Projekt
description: Informationen zum Zuweisen einer Python-Umgebung zur Verwendung in einem Visual Studio-Projekt sowie Anweisungen zum Erstellen virtueller Umgebungen
ms.date: 03/21/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 85ac0ab5fe06db5af677290a99f914616e3ed064
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-assign-which-python-environment-is-used-for-a-project"></a>Zuweisen einer Python-Umgebung für ein Projekt

Der gesamte Code in einem Python-Projekt wird im Kontext einer bestimmten Umgebung ausgeführt. Visual Studio verwendet diese Umgebung auch für das Debugging, für Import- und Membervervollständigungen, für Syntaxüberprüfungen sowie für weitere Tasks, die eine Umgebung erfordern.

Alle neuen Python-Projekte in Visual Studio werden anfänglich für die Verwendung der globalen Standardumgebung konfiguriert, die im Projektmappen-Explorer unter dem Knoten **Python-Umgebungen** angezeigt wird:

![Globale Python-Standardumgebung im Projektmappen-Explorer](media/environments-project.png)

Klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und klicken Sie auf **Python-Umgebungen hinzufügen/entfernen...**, um die Umgebung eines Projekts zu entfernen. Wählen Sie aus der angezeigten Liste, die globale, virtuelle und Conda-Umgebungen enthält, diejenigen aus, die im Knoten **Python-Umgebungen** angezeigt werden sollen:

![Dialogfeld „Python-Umgebungen hinzufügen/entfernen“](media/environments-add-remove.png)

Nachdem Sie auf **OK** geklickt haben, werden alle ausgewählten Umgebungen unter dem Knoten **Python-Umgebungen** angezeigt. Die aktuell aktivierte Umgebung wird fett formatiert angezeigt:

![Mehrere Python-Umgebungen im Projektmappen-Explorer](media/environments-project-multiple.png)

Klicken Sie mit der rechten Maustaste auf den Namen der Umgebung, und wählen Sie **Umgebung aktivieren** aus, um eine andere Umgebung schnell zu aktivieren. Ihre Auswahl wird mit dem Projekt gespeichert, und wann immer Sie das Projekt in Zukunft öffnen, ist diese Umgebung aktiviert. Wenn Sie alle Optionen im Dialogfeld **Python-Umgebungen hinzufügen/entfernen** deaktivieren, aktiviert Visual Studio die globale Standardumgebung.

Das Kontextmenü des Knotens **Python-Umgebungen** stellt ebenfalls zusätzliche Befehle bereit:

| Befehl | description |
| --- | --- |
| Virtuelle Umgebung hinzufügen... | Startet den Prozess zum Erstellen einer neuen virtuellen Umgebung im Projekt Weitere Informationen finden Sie unter [Create a virtual environment (Erstellen einer virtuellen Umgebung)](#create-a-virtual-environment). |
| Vorhandene virtuelle Umgebung hinzufügen... | Fordert Sie dazu auf, einen Ordner auszuwählen, der eine virtuelle Umgebung enthält, und fügt diese der Liste unter **Python-Umgebungen** hinzu, ohne diese zu aktivieren Weitere Informationen finden Sie unter [ActivateAdd an existing virtual environment (Aktivieren einer vorhandenen virtuellen Umgebung)](#activate-an-existing-virtual-environment). |
| Conda-Umgebung erstellen... | Wechselt zum **Fenster** *Python-Umgebungen*, in dem Sie einen Namen für die Umgebung eingeben und deren Basisinterpreter angeben |

## <a name="using-virtual-environments"></a>Verwenden von virtuellen Umgebungen

Eine virtuelle Umgebung ist eine einzigartige Kombination aus einem bestimmten Python-Interpreter und einem bestimmten Satz Bibliotheken, die sich von anderen globalen und Conda-Umgebungen unterscheidet. Eine virtuelle Umgebung ist für ein Projekt spezifisch und wird in einem Projektordner gespeichert. Dieser Ordner enthält die installierten Bibliotheken der Umgebung sowie eine `pyvenv.cfg`-Datei, die den Pfad zum *Basisinterpreter* der Umgebung angibt, der sich an anderer Stelle im Dateisystem befindet. (Das bedeutet, dass eine virtuelle Umgebung keine Kopie des Interpreters enthält, sondern nur einen Link zu diesem.) 

Ein Vorteil bei der Verwendung einer virtuellen Umgebung liegt daran, dass diese immer die genauen Abhängigkeiten des Projekts angibt, während Sie das Projekt entwickeln. (Im Gegensatz dazu enthält eine gemeinsam genutzte globale Umgebung alle Bibliotheken, unabhängig davon, ob Sie diese im Projekt verwenden.) Über die virtuelle Umgebung können Sie dann einfach eine `requirements.txt`-Datei erstellen, die dazu verwendet wird, diese Abhängigkeiten auf einem anderen Entwicklungs- oder Produktionscomputer erneut zu installieren. Weitere Informationen finden Sie unter [Verwalten von erforderlichen Paketen mit „requirements.txt“](managing-required-packages-with-requirements-txt.md).

Wenn Sie ein Projekt in Visual Studio öffnen, das eine `requirements.txt`-Datei enthält, stellt Visual Studio Ihnen die Option bereit, die virtuelle Umgebung neu zu erstellen. Auf Computern, auf denen Visual Studio nicht installiert ist (z.B. Azure App Service), können Sie `pip install -r requirements.txt` verwenden, um die Pakete wiederherzustellen (dieser Prozess wird unter [Verwalten von Python auf Azure App Service](managing-python-on-azure-app-service.md) beschrieben).

Da eine virtuelle Umgebung einen hartcodierten Pfad zum Basisinterpreter enthält, und da Sie die Umgebung mithilfe von `requirements.txt` neu erstellen können, lassen Sie üblicherweise den gesamten Ordner der virtuellen Umgebung aus der Quellcodeverwaltung aus.

In den folgenden Abschnitten wird erklärt, wie eine vorhandene virtuelle Umgebung in einem Projekt aktiviert wird und wie eine neue virtuelle Umgebung erstellt wird.

In Visual Studio kann eine virtuelle Umgebung wie jede andere Umgebung über den Knoten **Python-Umgebungen** im **Projektmappen-Explorer** für ein Projekt aktiviert werden.

Sobald eine virtuelle Umgebung zu Ihrem Projekt hinzugefügt wird, wird diese im Fenster **Python-Umgebungen** angezeigt. Sie können diese dann wie jede andere Umgebung aktivieren und die enthaltenen Pakete verwalten.

### <a name="create-a-virtual-environment"></a>Erstellen einer virtuellen Umgebung

Sie können eine neue Umgebung wie folgt direkt in Visual Studio erstellen:

1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Python-Umgebungen**, und wählen Sie **Virtuelle Umgebung hinzufügen...** aus. Daraufhin wird folgendes Dialogfeld angezeigt:

    ![Erstellen einer virtuellen Umgebung](media/environments-add-virtual-1.png)

1. Geben Sie im Feld **Speicherort der virtuellen Umgebung** einen Pfad für die virtuelle Umgebung an. Wenn Sie nur einen Namen angeben, wird die virtuelle Umgebung innerhalb des aktuellen Projekts in einem Unterordner dieses Namens erstellt.

1. Wählen Sie eine Umgebung als Basisinterpreter aus, und klicken Sie auf **Erstellen**. Visual Studio zeigt eine Statusanzeige an, während die Umgebung erstellt wird und alle erforderlichen Pakete heruntergeladen werden. Zu diesem Zeitpunkt wird die virtuelle Umgebung im Fenster **Python-Umgebungen** für das Projekt angezeigt, das die Umgebung enthält.

1. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Um sie für das Projekt zu aktivieren, klicken Sie mit der rechten Maustaste darauf und wählen **Umgebung aktivieren** aus.

> [!Note]
> Wenn der Pfad zum Speicherort eine vorhandene virtuelle Umgebung identifiziert, erkennt Visual Studio den Basisinterpreter automatisch (mithilfe der `orig-prefix.txt`-Datei im Verzeichnis `lib` der Umgebung) und ändert die Schaltfläche „Erstellen“ zu **Hinzufügen**.
>
> Wenn Sie eine virtuelle Umgebung hinzufügen und eine `requirements.txt`-Datei vorhanden ist, zeigt das Dialogfeld **Virtuelle Umgebung hinzufügen** eine Option zur automatischen Paketinstallation an. Auf diese Weise kann eine Umgebung ganz einfach auf einem anderen Computer neu erstellt werden:
>
> ![Erstellen einer virtuellen Umgebung mit „requirements.txt“](media/environments-requirements-txt.png)
>
> Das Ergebnis ist das gleiche wie bei der Verwendung des Befehls **Vorhandene virtuelle Umgebung hinzufügen...**.

### <a name="activate-an-existing-virtual-environment"></a>Aktivieren einer vorhandenen virtuellen Umgebung

Wenn Sie bereits an anderer Stelle eine virtuelle Umgebung erstellt haben, können Sie diese wie folgt für ein Projekt aktivieren:

1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Python-Umgebungen**, und wählen Sie **Vorhandene virtuelle Umgebung hinzufügen...** aus.

1. Navigieren Sie im angezeigten Dialogfeld **Durchsuchen** zu dem Ordner, der die virtuelle Umgebung enthält, wählen Sie ihn aus, und klicken Sie auf **OK**. Wenn Visual Studio eine `requirements.txt`-Datei in dieser Umgebung erkennt, werden Sie gefragt, ob diese Paket installiert werden sollen.

1. Nach kurzer Zeit wird die virtuelle Umgebung im Projektmappen-Explorer unter dem Knoten **Python-Umgebungen** angezeigt. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Klicken Sie daher mit der rechten Maustaste auf die Umgebung, und wählen Sie **Umgebung aktivieren** aus.

### <a name="remove-a-virtual-environment"></a>Entfernen einer virtuellen Umgebung

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die virtuelle Umgebung, und wählen Sie **Entfernen** aus.

1. Sie werden von Visual Studio gefragt, ob Sie die virtuelle Umgebung entfernen oder löschen möchten. Wenn Sie **Entfernen** auswählen, ist die Umgebung für das Projekt nicht mehr verfügbar, verbleibt aber im Dateisystem. Wenn Sie **Löschen** auswählen, wird die Umgebung sowohl aus dem Projekt entfernt als auch aus dem Dateisystem gelöscht. Der Basisinterpreter bleibt unverändert.

## <a name="view-installed-packages"></a>Anzeigen installierter Pakete

Erweitern Sie im Projektmappen-Explorer den Knoten einer bestimmten Umgebung, um die in dieser Umgebung installierten Pakete anzuzeigen (dies bedeutet, dass Sie diese Pakete importieren und in Ihrem Code verwenden können, wenn die Umgebung aktiv ist):

![Python-Pakete für eine Umgebung im Projektmappen-Explorer](media/environments-installed-packages.png)

Um neue Pakete zu installieren, klicken Sie mit der rechten Maustaste auf die Umgebung, und wählen Sie **Python-Paket installieren...** aus, um zur Registerkarte **Pakete** im Fenster **Python-Umgebungen** zu wechseln. Geben Sie einen Suchbegriff ein (in der Regel den Paketnamen), und Visual Studio zeigt entsprechende Pakete an.

Pakete (und Abhängigkeiten) werden in Visual Studio vom [Python Package Index (PyPI)](https://pypi.org) heruntergeladen. Dort können Sie auch nach verfügbaren Paketen suchen. Statusleiste und Ausgabefenster von Visual Studio zeigen Informationen zur Installation an. Um ein Paket zu deinstallieren, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Entfernen** aus.

Hinweis: Die angezeigten Einträge sind nicht immer unbedingt richtig, und eine Installation oder Deinstallation ist möglicherweise unzuverlässig oder unmöglich. Visual Studio verwendet den pip-Paket-Manager, falls verfügbar, und lädt ihn bei Bedarf herunter und installiert ihn. Visual Studio kann auch den easy_install-Paket-Manager verwenden. Pakete, die mit `pip` oder `easy_install` über die Befehlszeile installiert wurden, werden ebenfalls angezeigt.

Beachten Sie auch, dass Visual Studio die Verwendung von `conda` zum Installieren von Paketen in einer Conda-Umgebung derzeit nicht unterstützt. Verwenden Sie stattdessen `conda` über die Befehlszeile.

> [!Tip]
> Eine gängige Situation, in der pip ein Paket nicht installieren kann, liegt vor, wenn das Paket Quellcode für native Komponenten in `*.pyd`-Dateien enthält. Wenn die erforderliche Version von Visual Studio nicht installiert ist, kann pip diese Komponenten nicht kompilieren. Die Fehlermeldung, die in derartigen Situationen angezeigt wird, ist `error: Unable to find vcvarsall.bat`. `easy_install` kann häufig vorkompilierte Binärdateien herunterladen, und Sie können einen geeigneten Compiler für ältere Python-Versionen von [http://aka.ms/VCPython27](http://aka.ms/VCPython27) herunterladen. Weitere Informationen finden Sie unter [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Umgang mit der Fehlermeldung, dass vcvarsallbat nicht gefunden werden konnte) im Teamblog zu Python-Tools.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Verwenden von "requirements.txt" für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)