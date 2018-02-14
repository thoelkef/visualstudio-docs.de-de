---
title: Verwenden von PyLint mit Python-Code in Visual Studio | Microsoft-Dokumentation
description: "Verwenden von PyLint in Visual Studio zum Überprüfen von Problemen in Python-Code."
ms.custom: 
ms.date: 07/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
dev_langs:
- python
ms.tgt_pltfrm: 
ms.topic: article
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload:
- python
- data-science
ms.openlocfilehash: ec8737db3db3da99ad372b24b9308fc93811ebc4
ms.sourcegitcommit: 205d15f4558315e585c67f33d5335d5b41d0fcea
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2018
---
# <a name="using-pylint-to-check-python-code"></a>Verwenden von PyLint zur Überprüfung von Python-Code

[PyLint](https://www.pylint.org/), ein häufig verwendetes Tool, das Python-Code auf Fehler überprüft und gute Python-Codemuster unterstützt, ist in Visual Studio für Python-Projekte integriert.

Klicken Sie einfach im Projektmappen-Explorer mit der rechten Maustaste auf ein Python-Projekt, und wählen Sie **Python > PyLint ausführen...** aus:

![PyLint-Befehl im Kontextmenü für Python-Projekte](media/code-pylint-command.png)

Wenn Sie diesen Befehl verwenden, werden Sie dazu aufgefordert, PyLint in Ihrer aktiven Umgebung zu installieren, wenn es noch nicht vorhanden ist.

PyLint-Warnungen und -Fehler werden im Fehlerlistenfenster angezeigt:

![PyLint-Fehlerliste](media/code-pylint-error-list.png)

Durch Doppelklicken auf einen Fehler gelangen Sie direkt zu dem Quellcode, der das Problem verursacht.

> [!Tip]
> Eine detaillierte Liste aller PyLint-Ausgabemeldungen finden Sie in der [PyLint-Funktionsreferenz](https://pylint.readthedocs.io/en/latest/technical_reference/features.html).

## <a name="setting-pylint-command-line-options"></a>Festlegen von PyLint-Befehlszeilenoptionen

Der Abschnitt mit [Befehlszeilenoptionen](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) in der PyLint-Dokumentation beschreibt, wie das Verhalten von PyLint über eine `.pylintrc`-Konfigurationsdatei gesteuert wird. Eine solche Datei kann im Stammverzeichnis eines Python-Projekts in Visual Studio oder in einem anderen Verzeichnis platziert werden, je nachdem, in welchem Umfang die Einstellungen angewendet werden sollen (Details finden Sie in den [Befehlszeilenoptionen](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options)).

Um z.B. die in der obigen Abbildung gezeigten „missing-docstring“-Warnungen mit einer `.pylintrc`-Datei in einem Projekt zu unterdrücken, gehen Sie folgendermaßen vor:

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis Ihres Projekts (dort finden Sie Ihre `.pyproj`-Datei), und führen Sie den folgenden Befehl aus, um eine kommentierte Konfigurationsdatei zu generieren:

   ```command
   pylint --generate-rcfile > .pylintrc
   ```

1. Klicken Sie im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Hinzufügen > Vorhandenes Element...**, navigieren Sie zur neuen `.pylintrc`-Datei, wählen Sie sie aus, und klicken Sie auf **Hinzufügen**.

1. Öffnen Sie die Datei zum Bearbeiten, die unterschiedliche Einstellungen enthält, mit denen Sie arbeiten können. Um eine Warnung zu deaktivieren, suchen Sie den Abschnitt `[MESSAGES CONTROL]` und darin die Einstellung `disable`. Es gibt eine lange Zeichenfolge mit spezifischen Meldungen, an die Sie beliebige Warnungen anfügen können. Im vorliegenden Beispiel wird `,missing-docstring` angefügt (einschließlich des trennenden Kommas).

1. Speichern Sie die `.pylintrc`-Datei, und führen Sie PyLint erneut aus. Sie werden feststellen, dass die Warnungen jetzt unterdrückt werden.

> [!Tip]
> Um eine `.pylintrc`-Datei aus einer Netzwerkfreigabe zu verwenden, erstellen Sie auf der Netzwerkfreigabe eine Umgebungsvariable namens `PYLINTRC` mit dem Wert des Dateinamens und verwenden dazu einen UNC-Pfad oder einen zugeordneten Laufwerkbuchstaben. Beispielsweise `PYLINTRC=\\myshare\python\.pylintrc`.
