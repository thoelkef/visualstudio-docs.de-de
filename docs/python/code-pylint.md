---
title: Verwenden von PyLint in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/12/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc668a4b-10ae-4199-90b8-c984456b6003
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: cd841938f160420934941a5166184f79aca82be7
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

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
> Eine detaillierte Liste aller PyLint-Ausgabemeldungen finden Sie in der [PyLint-Funktionsreferenz](https://pylint.readthedocs.io/en/latest/reference_guide/features.html).

## <a name="setting-pylint-command-line-options"></a>Festlegen von PyLint-Befehlszeilenoptionen

Der Abschnitt mit [Befehlszeilenoptionen](https://pylint.readthedocs.io/en/latest/user_guide/run.html#command-line-options) in der PyLint-Dokumentation beschreibt, wie das Verhalten von PyLint über eine `.pylintrc`-Konfigurationsdatei gesteuert wird. Eine solche Datei kann im Stammverzeichnis eines Python-Projekts in Visual Studio oder in einem anderen Verzeichnis platziert werden, je nachdem, in welchem Umfang die Einstellungen angewendet werden sollen.

Um z.B. die in der obigen Abbildung gezeigten „missing-docstring“-Warnungen mit einer `.pylintrc`-Datei in einem Projekt zu unterdrücken, gehen Sie folgendermaßen vor:

1. Navigieren Sie in der Befehlszeile zum Stammverzeichnis Ihres Projekts (dort finden Sie Ihre `.pyproj`-Datei), und führen Sie den folgenden Befehl aus, um eine kommentierte Konfigurationsdatei zu generieren:

   ```bash
   pylint --generate-rcfile > .pylintrc
   ```

1. Klicken Sie im Visual Studio-Projektmappen-Explorer mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Hinzufügen > Vorhandenes Element...**, navigieren Sie zur neuen `.pylintrc`-Datei, wählen Sie sie aus, und klicken Sie auf **Hinzufügen**.

1. Öffnen Sie die Datei zum Bearbeiten, die unterschiedliche Einstellungen enthält, mit denen Sie arbeiten können. Um eine Warnung zu deaktivieren, suchen Sie den Abschnitt `[MESSAGES CONTROL]` und darin die Einstellung `disable`. Es gibt eine lange Zeichenfolge mit spezifischen Meldungen, an die Sie beliebige Warnungen anfügen können. Im vorliegenden Beispiel wird `,missing-docstring` angefügt (einschließlich des trennenden Kommas).

1. Speichern Sie die `.pylintrc`-Datei, und führen Sie PyLint erneut aus. Sie werden feststellen, dass die Warnungen jetzt unterdrückt werden.
