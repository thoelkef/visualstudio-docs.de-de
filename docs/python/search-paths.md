---
title: Verwenden von Python-Suchpfaden
description: Überblick über den Einsatz von Python-Suchpfaden in Visual Studio in Umgebungen und Projekten.
ms.date: 11/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: ab55c7cf1daa02416e6192a02a01ee3f9a35f6f0
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607900"
---
# <a name="how-visual-studio-uses-python-search-paths"></a>Verwenden von Python-Suchpfaden in Visual Studio

Bei der typischen Python-Nutzung stellt die `PYTHONPATH`-Umgebungsvariable (oder `IRONPYTHONPATH` usw.) den Standardsuchpfad für Moduldateien bereit. Wenn Sie also die Anweisungen `from <name> import...` oder `import <name>` verwenden, durchsucht Python der Reihe nach die folgenden Speicherorte nach einem übereinstimmenden Namen:

1. Die integrierten Python-Module.
1. Den Ordner, der den Python-Code enthält, den Sie ausführen.
1. Den „Modulsuchpfad“, gemäß der Definition durch die entsprechenden Umgebungsvariablen. (Weitere Informationen finden Sie unter [The Module Search Path](https://docs.python.org/2/tutorial/modules.html#the-module-search-path) (Modulsuchpfad) und [Environment variables](https://docs.python.org/2/using/cmdline.html#envvar-PYTHONPATH) (Umgebungsvariablen) in der Python-Hauptdokumentation.)

Die Umgebungsvariable für den Suchpfad wird von Visual Studio jedoch ignoriert, auch wenn sie für das gesamte System festgelegt wurde. Tatsächlich wird sie ignoriert, gerade *weil* sie für das gesamte System festgelegt wurde und sich daher bestimmte Fragen stellen, die nicht automatisch beantwortet werden können: Sind die referenzierten Module für Python 2.7 oder Python 3.6 und höher vorgesehen? Werden sie die standardmäßigen Bibliotheksmodule überschreiben? Weiß der Entwickler das, oder handelt es sich um einen böswilligen Hijackingversuch?

Visual Studio bietet daher eine Möglichkeit, Suchpfade direkt in Umgebungen und Projekten anzugeben. Suchpfade werden als Wert von `PYTHONPATH` (oder anderen entsprechenden Variablen) beim Debuggen oder Ausführen des Skripts in Visual Studio übergeben. Durch das Hinzufügen von Suchpfaden überprüft Visual Studio die Bibliotheken an diesen Speicherorten und erstellt ggf. entsprechende IntelliSense-Datenbanken für sie (Visual Studio 2017 Version 15.5 und früher; das Erstellen der Datenbank kann je nach Anzahl der Bibliotheken einige Zeit in Anspruch nehmen).

Wenn Sie einen Suchpfad hinzufügen möchten, wechseln Sie zum **Projektmappen-Explorer**, erweitern Sie Ihren Projektknoten, klicken Sie mit der rechten Maustaste auf **Suchpfade**, und wählen Sie **Add Folder to Search Path** (Ordner zu Suchpfad hinzufügen) aus:

![Befehl zum Hinzufügen eines Ordners zum Suchpfad in Suchpfaden im Projektmappen-Explorer](media/search-paths-command.png)

Mit diesem Befehl wird ein Browser angezeigt, in dem Sie anschließend den einzuschließenden Ordner auswählen.

Wenn Ihre Umgebungsvariable `PYTHONPATH` bereits Ihren bzw. Ihre gewünschten Ordner enthält, können Sie die Option **Add PYTHONPATH to Search Paths** (PYTHONPATH zu Suchpfaden hinzufügen) als praktische Verknüpfung verwenden.

Sobald Ordner zu den Suchpfaden hinzugefügt wurden, verwendet Visual Studio diese Pfade für jede Umgebung, die dem Projekt zugeordnet ist. (Möglicherweise werden Ihnen Fehlermeldungen angezeigt, wenn die Umgebung auf Python 3 basiert, und Sie versuchen, Python 2.7-Modulen einen Suchpfad hinzuzufügen.)

Dateien mit einer *ZIP*- oder *EGG*-Erweiterung können ebenfalls als Suchpfade hinzugefügt werden. Wählen Sie hierzu **Add ZIP Archive to Search Path** (ZIP-Archiv zu Suchpfad hinzufügen) aus. Wie bei Ordnern wird der Inhalt dieser Dateien geprüft und IntelliSense zur Verfügung gestellt.

## <a name="see-also"></a>Siehe auch

- [Verwalten von Python-Umgebungen in Visual Studio](managing-python-environments-in-visual-studio.md)
- [Auswählen eines Interpreters für ein Projekt](selecting-a-python-environment-for-a-project.md)
- [Verwenden von „requirements.txt“ für Abhängigkeiten](managing-required-packages-with-requirements-txt.md)
- [Das Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md)
