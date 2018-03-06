---
title: "Auswählen einer Umgebung für ein Projekt | Microsoft-Dokumentation"
description: "Im Visual Studio-Projektmappen-Explorer können Sie einen bestimmten Python-Interpreter (eine Umgebung) zuweisen, die immer für alle Projekte verwendet wird. Die Standardumgebung wird ignoriert. Sie können auch virtuelle Umgebungen erstellen und verwalten."
ms.custom: 
ms.date: 02/20/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: 6f422cc60638b7eed4a5b42516e7496c4a6f6209
ms.sourcegitcommit: c0a2385a16cc4f47d2e1ff23d35c4da40f5605e0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/23/2018
---
# <a name="selecting-a-python-interpreter-and-environment-for-use-in-a-project"></a>Auswählen eines Python-Interpreters und einer Umgebung zur Verwendung in einem Projekt

Der gesamte Code in einem Python-Projekt wird im Kontext einer bestimmten Umgebung ausgeführt. Visual Studio verwendet diese Umgebung auch für das Debugging, für Import- und Membervervollständigungen, für Syntaxüberprüfungen sowie für weitere Tasks, die eine Umgebung erfordern.

Alle neuen Python-Projekte in Visual Studio werden anfänglich für die Verwendung der globalen Standardumgebung konfiguriert, die im Projektmappen-Explorer unter dem Knoten **Python-Umgebungen** angezeigt wird:

![Globale Python-Standardumgebung im Projektmappen-Explorer](media/environments-project.png)

Sie können weitere Umgebungen, einschließlich virtueller Umgebungen, für das Projekt verfügbar machen. Es kann immer nur eine Umgebung gleichzeitig aktiviert sein.

## <a name="using-global-environments"></a>Verwenden von globalen Umgebungen

Um bestimmte globale Umgebungen für das Projekt verfügbar zu machen (einschließlich [manuell identifizierter](managing-python-environments-in-visual-studio.md#manually-identifying-an-existing-environment) Conda-Umgebungen), klicken Sie mit der rechten Maustaste auf den Knoten **Python-Umgebungen**, und wählen Sie **Python-Umgebungen hinzufügen/entfernen...**. Wählen Sie die gewünschten Umgebungen aus der angezeigten Liste aus:

![Dialogfeld „Python-Umgebungen hinzufügen/entfernen“](media/environments-add-remove.png)

Nachdem Sie auf **OK** geklickt haben, werden alle ausgewählten Umgebungen unter dem Knoten **Python-Umgebungen** angezeigt. Die aktuell aktivierte Umgebung wird fett formatiert angezeigt:

![Mehrere Python-Umgebungen im Projektmappen-Explorer](media/environments-project-multiple.png)

Um eine andere Umgebung zu aktivieren, klicken Sie mit der rechten Maustaste auf den Namen der Umgebung, und wählen Sie **Umgebung aktivieren** aus. Ihre Auswahl wird mit dem Projekt gespeichert, und wann immer Sie das Projekt in Zukunft öffnen, ist diese Umgebung aktiviert.

Wenn Sie alle Optionen im Dialogfeld **Python-Umgebungen hinzufügen/entfernen** deaktivieren, aktiviert Visual Studio die globale Standardumgebung.

## <a name="using-virtual-environments"></a>Verwenden von virtuellen Umgebungen

Eine virtuelle Umgebung ist eine einzigartige Kombination aus einem bestimmten Python-Interpreter und einem bestimmten Satz Bibliotheken, die sich von anderen globalen und Conda-Umgebungen unterscheidet. Sie verwenden eine virtuelle Umgebung in der Regel dann, wenn für ein Projekt bestimmte Anforderungen bestehen und Sie keine andere Umgebung ändern möchten, um diese Anforderungen zu erfüllen.

Sobald eine virtuelle Umgebung Ihrem Projekt hinzugefügt wurde, erscheint sie im Fenster **Python-Umgebungen**. Sie können sie wie jede andere Umgebung aktivieren, und Sie können ihre Pakete verwalten.

Beachten Sie, dass ein Nachteil virtueller Umgebungen darin besteht, dass sie hartcodierte Dateipfade enthalten und somit nicht problemlos freigegeben oder auf andere Entwicklungscomputer übertragen werden können. Sie können die `requirements.txt`-Datei verwenden, um Empfängern Ihres Projekts zu erlauben, die Umgebung problemlos wiederherzustellen. Weitere Informationen finden Sie unter [Verwalten von erforderlichen Paketen mit „requirements.txt“](managing-required-packages-with-requirements-txt.md).

### <a name="activating-an-existing-virtual-environment"></a>Aktivieren einer vorhandenen virtuellen Umgebung

Wenn Sie bereits an anderer Stelle eine virtuelle Umgebung erstellt haben, können Sie diese wie folgt für ein Projekt aktivieren:

1. Klicken Sie mit der rechten Maustaste im Projektmappen-Explorer auf **Python-Umgebungen**, und wählen Sie **Vorhandene virtuelle Umgebung hinzufügen...** aus.

1. Navigieren Sie im angezeigten Dialogfeld **Durchsuchen** zu dem Ordner, der die virtuelle Umgebung enthält, wählen Sie ihn aus, und klicken Sie auf **OK**. Wenn Visual Studio eine `requirements.txt`-Datei in dieser Umgebung erkennt, werden Sie gefragt, ob diese Paket installiert werden sollen.

1. Nach kurzer Zeit wird die virtuelle Umgebung im Projektmappen-Explorer unter dem Knoten **Python-Umgebungen** angezeigt. Die virtuelle Umgebung ist nicht standardmäßig aktiviert. Klicken Sie daher mit der rechten Maustaste auf die Umgebung, und wählen Sie **Umgebung aktivieren** aus.

### <a name="creating-a-virtual-environment"></a>Erstellen einer virtuellen Umgebung

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

### <a name="remove-a-virtual-environment"></a>Entfernen einer virtuellen Umgebung

1. Klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf die virtuelle Umgebung, und wählen Sie **Entfernen** aus.

1. Sie werden von Visual Studio gefragt, ob Sie die virtuelle Umgebung entfernen oder löschen möchten. Wenn Sie **Entfernen** auswählen, ist die Umgebung für das Projekt nicht mehr verfügbar, verbleibt aber im Dateisystem. Wenn Sie **Löschen** auswählen, wird die Umgebung sowohl aus dem Projekt entfernt als auch aus dem Dateisystem gelöscht. Der Basisinterpreter bleibt unverändert.

## <a name="viewing-installed-packages"></a>Anzeigen installierter Pakete

Erweitern Sie im Projektmappen-Explorer den Knoten einer bestimmten Umgebung, um die in dieser Umgebung installierten Pakete anzuzeigen (dies bedeutet, dass Sie diese Pakete importieren und in Ihrem Code verwenden können, wenn die Umgebung aktiv ist):

![Python-Pakete für eine Umgebung im Projektmappen-Explorer](media/environments-installed-packages.png)

Um neue Pakete zu installieren, klicken Sie mit der rechten Maustaste auf die Umgebung, und wählen Sie **Python-Paket installieren...** aus, um zur Registerkarte **Pakete** im Fenster **Python-Umgebungen** zu wechseln. Geben Sie einen Suchbegriff ein (in der Regel den Paketnamen), und Visual Studio zeigt entsprechende Pakete an.

Pakete (und Abhängigkeiten) werden in Visual Studio vom [Python Package Index (PyPI)](https://pypi.python.org/pypi) heruntergeladen. Dort können Sie auch nach verfügbaren Paketen suchen. Statusleiste und Ausgabefenster von Visual Studio zeigen Informationen zur Installation an. Um ein Paket zu deinstallieren, klicken Sie mit der rechten Maustaste darauf, und wählen Sie **Entfernen** aus.

Hinweis: Die angezeigten Einträge sind nicht immer unbedingt richtig, und eine Installation oder Deinstallation ist möglicherweise unzuverlässig oder unmöglich. Visual Studio verwendet den pip-Paket-Manager, falls verfügbar, und lädt ihn bei Bedarf herunter und installiert ihn. Visual Studio kann auch den easy_install-Paket-Manager verwenden. Pakete, die mit `pip` oder `easy_install` über die Befehlszeile installiert wurden, werden ebenfalls angezeigt.

Beachten Sie auch, dass Visual Studio die Verwendung von `conda` zum Installieren von Paketen in einer Conda-Umgebung derzeit nicht unterstützt. Verwenden Sie stattdessen `conda` über die Befehlszeile.

> [!Tip]
> Eine gängige Situation, in der pip ein Paket nicht installieren kann, liegt vor, wenn das Paket Quellcode für native Komponenten in `*.pyd`-Dateien enthält. Wenn die erforderliche Version von Visual Studio nicht installiert ist, kann pip diese Komponenten nicht kompilieren. Die Fehlermeldung, die in derartigen Situationen angezeigt wird, ist `error: Unable to find vcvarsall.bat`. `easy_install` ist häufig in der Lage, vorkompilierte Binärdateien herunterzuladen, und Sie können einen geeigneten Compiler für ältere Python-Versionen von [http://aka.ms/VCPython27](http://aka.ms/VCPython27) herunterladen. Weitere Informationen finden Sie unter [How to deal with the pain of "unable to find vcvarsallbat"](https://blogs.msdn.microsoft.com/pythonengineering/2016/04/11/unable-to-find-vcvarsall-bat/) (Umgang mit der Fehlermeldung, dass vcvarsallbat nicht gefunden werden konnte) im Teamblog zu Python-Tools.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Verwenden von "requirements.txt" für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Suchpfade](search-paths.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)