---
title: "Symbole für den gemischten Python-C++-Debugmodus in Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 4/4/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be5fdf2f-b55f-488a-9772-58adfe07a7ab
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: adf122a478b29674dc2924dcf7d42972a5a3f52e
ms.openlocfilehash: b8bf362f506255c09468934f01a7beeef3a632dd
ms.lasthandoff: 04/10/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Installieren von Debugsymbolen für Python-Interpreter

Um ein vollständiges Debuggen zu ermöglichen, muss der [Python-Debugger für den gemischten Modus](debugging-mixed-mode.md) in Visual Studio zahlreiche interne Datenstrukturen im verwendeten Python-Interpreter analysieren. Dazu sind Debugsymbole für den Interpreter selbst erforderlich. Für python27.dll ist die entsprechende Symboldatei zum Beispiel python27.pdb, und für python36.dll ist die Symboldatei python36.pdb. Jede Version des Interpreters bietet auch Symboldateien für eine Vielzahl von Modulen.

Mit Visual Studio 2017 installieren die Interpreter „Python 3“ und „Anaconda 3“ automatisch die entsprechenden Symbole, und Visual Studio findet diese automatisch. Für Visual Studio 2015 und frühere Versionen oder bei Verwendung anderer Interpreter müssen Sie Symbole separat herunterladen und dann Visual Studio über das Dialogfeld **Tools > Optionen** in der Registerkarte **Debuggen > Symbole** darauf aufmerksam machen. Diese Schritte werden in den folgenden Abschnitten ausführlich beschrieben.

Visual Studio fordert Sie möglicherweise zur Eingabe auf, wenn diese Symbole benötigt werden. In der Regel ist dies beim Starten einer Debugsitzung im gemischten Modus der Fall. In diesem Fall wird ein Dialogfeld mit zwei Optionen angezeigt:

- Über **Dialogfeld mit Symboleinstellungen öffnen** wird das Dialogfeld **Optionen** der Registerkarte **Debuggen > Symbole** geöffnet.
- Über **Symbole für meinen Interpreter herunterladen** wird diese aktuelle Dokumentationsseite geöffnet. Wählen Sie in diesem Fall **Tools > Optionen** aus, und navigieren Sie zur Registerkarte **Debuggen > Symbole**, um fortzufahren.

    ![Aufforderung für Debugsymbole im gemischten Modus](~/python/media/mixed-mode-debugging-symbols-required.png)

## <a name="downloading-symbols"></a>Symbole werden heruntergeladen.

- Python 3.5 und höher: Debugsymbole über das Python-Installationsprogramm erhalten. Wählen Sie **Benutzerdefinierte Installation** und **Weiter**, um zu **Erweiterte Optionen** zu gelangen, und aktivieren Sie dann die Kontrollkästchen für **Debugsymbole herunterladen** und **Debugbinärdateien herunterladen**:

    ![Installationsprogramm für Python 3.x mit Debugsymbolen](~/python/media/mixed-mode-debugging-symbols-installer35.png)

    Die Symboldateien (`.pdb`) befinden sich dann im Stammordner für die Installation (Symboldateien für einzelne Module befinden sich auch im `DLLs`-Ordner). Aus diesem Grund werden sie von Visual Studio automatisch gefunden, und es sind keine weiteren Schritte erforderlich.

- Python 3.4.x und früher: Symbole sind als herunterladbare ZIP-Dateien aus [Offizielle Distributionen](#official-distributions) oder [Enthought Canopy](#enthought-canopy) verfügbar, wie unten beschrieben. Extrahieren Sie nach dem Download die Dateien in einen lokalen Ordner, z.B. in einen `Symbols`-Ordner im Python-Ordner.

    > [!Important]
    > Symbole unterscheiden sich zwischen kleineren Builds von Python sowie zwischen 32- und 64-Bit-Builds, weshalb die Versionen genau übereinstimmen sollten. Erweitern Sie den *Knoten* **Python-Umgebungen** unterhalb des Projekts im Projektmappen-Explorer, und beachten Sie den Umgebungsnamen, um zu überprüfen, welcher Interpreter verwendet wird. Wechseln Sie dann zum *Fenster* **Python-Umgebungen**, und beachten Sie den Speicherort für die Installation. Öffnen Sie dann ein Befehlsfenster an diesem Speicherort, und starten Sie `python.exe`, wodurch die genaue Version angezeigt wird sowie ob es sich um einen 32- oder 64-Bit-Build handelt.

- Bei jeder anderen Python-Distribution eines Drittanbieters wie z.B. ActiveState Python müssen Sie sich an die Autoren dieser Distribution wenden und sie um die Symbole bitten. WinPython dagegen enthält den Python-Standardinterpreter in unveränderter Form. Verwenden Sie dafür also die Symbole der offiziellen Distribution für die entsprechende Versionsnummer.

## <a name="pointing-visual-studio-to-the-symbols"></a>Visual Studio auf die Symbole aufmerksam machen

Wenn Sie Symbole separat heruntergeladen haben, führen Sie folgende Schritte aus, um Visual Studio auf sie aufmerksam zu machen. Wenn Sie Symbole mit dem Installationsprogramm von Python 3.5 oder höher installiert haben, werden sie von Visual Studio automatisch gefunden.

1. Wählen Sie das Menü **Tools > Optionen** aus, und navigieren Sie zu **Debuggen > Symbole**.
    
1. Klicken Sie auf die Schaltfläche „Hinzufügen“ auf der Symbolleiste (siehe unten), geben Sie den Ordner an, in dem Sie die heruntergeladenen Symbole erweitert haben (in dem sich `python.pdb` befindet, also z.B. `c:\python34\Symbols` wie unten gezeigt), und klicken Sie auf **OK**. 

    ![Symboloptionen für den Debugger im gemischten Modus](~/python/media/mixed-mode-debugging-symbols.png)

1. Während einer Debugsitzung werden Sie von Visual Studio möglicherweise auch aufgefordert, den Speicherort einer Quelldatei für den Python-Interpreter anzugeben. Wenn Sie diese heruntergeladen haben (z.B. von [python.org/downloads](https://www.python.org/downloads)), können Sie natürlich auch diese angeben.

> [!Note]
> Die Funktionen zum Zwischenspeichern von Symbolen im Dialogfeld werden verwendet, um einen lokalen Cache für Symbole zu erstellen, die von einer Onlinequelle bezogen wurden. Diese Funktionen werden für die Symbole des Python-Interpreters nicht benötigt, da Sie diese bereits lokal heruntergeladen haben. In jedem Fall finden Sie weitere Informationen unter [Specify Symbols and Source Files in the Visual Studio Debugger (Angeben von Symbolen und Quelldateien im Visual Studio-Debugger)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).

## <a name="official-distributions"></a>Offizielle Distributionen

| Python-Version | Downloads | 
| --- | --- | 
| 3.5 und höher | Installieren Sie Symbole mit dem Python-Installationsprogramm. | 
| 3.4.4 | [32 Bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.4/python-3.4.4.amd64-pdb.zip) |
| 3.4.3 | [32 Bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.3/python-3.4.3.amd64-pdb.zip) |
| 3.4.2 | [32 Bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.2/python-3.4.2.amd64-pdb.zip) |
| 3.4.1 | [32 Bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.1/python-3.4.1.amd64-pdb.zip) |
| 3.4.0 | [32 Bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/3.4.0/python-3.4.0.amd64-pdb.zip) |
| 3.3.5 | [32 Bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5-pdb.zip) - [64 Bit](http://www.python.org/ftp/python/3.3.5/python-3.3.5.amd64-pdb.zip) |
| 3.3.4 | [32 Bit](http://python.org/ftp/python/3.3.4/python-3.3.4-pdb.zip) - [64 Bit](http://python.org/ftp/python/3.3.4/python-3.3.4.amd64-pdb.zip) |
| 3.3.3 | [32 Bit](http://python.org/ftp/python/3.3.3/python-3.3.3-pdb.zip) - [64 Bit](http://python.org/ftp/python/3.3.3/python-3.3.3.amd64-pdb.zip) |
| 3.3.2 | [32 Bit](http://python.org/ftp/python/3.3.2/python-3.3.2-pdb.zip) - [64 Bit](http://python.org/ftp/python/3.3.2/python-3.3.2.amd64-pdb.zip) |
| 3.3.1 | [32 Bit](http://python.org/ftp/python/3.3.1/python-3.3.1-pdb.zip) - [64 Bit](http://python.org/ftp/python/3.3.1/python-3.3.1.amd64-pdb.zip) |
| 3.3.0 | [32 Bit](http://python.org/ftp/python/3.3.0/python-3.3.0-pdb.zip) - [64 Bit](http://python.org/ftp/python/3.3.0/python-3.3.0.amd64-pdb.zip) |
| 2.7.11 | [32 Bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.11/python-2.7.11.amd64-pdb.zip) |
| 2.7.10 | [32 Bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.10/python-2.7.10.amd64-pdb.zip) |
| 2.7.9 | [32 Bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.9/python-2.7.9.amd64-pdb.zip) |
| 2.7.8 | [32 Bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.8/python-2.7.8.amd64-pdb.zip) |
| 2.7.7 | [32 Bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7-pdb.zip) - [64 Bit](https://www.python.org/ftp/python/2.7.7/python-2.7.7.amd64-pdb.zip) |
| 2.7.6 | [32 Bit](http://python.org/ftp/python/2.7.6/python-2.7.6-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.6/python-2.7.6.amd64-pdb.zip) |
| 2.7.5 | [32 Bit](http://python.org/ftp/python/2.7.5/python-2.7.5-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.5/python-2.7.5.amd64-pdb.zip) |
| 2.7.4 | [32 Bit](http://python.org/ftp/python/2.7.4/python-2.7.4-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.4/python-2.7.4.amd64-pdb.zip) |
| 2.7.3 | [32 Bit](http://python.org/ftp/python/2.7.3/python-2.7.3-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.3/python-2.7.3.amd64-pdb.zip) |
| 2.7.2 | [32 Bit](http://python.org/ftp/python/2.7.2/python-2.7.2-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.2/python-2.7.2.amd64-pdb.zip) |
| 2.7.1 | [32 Bit](http://python.org/ftp/python/2.7.1/python-2.7.1-pdb.zip) - [64 Bit](http://python.org/ftp/python/2.7.1/python-2.7.1.amd64-pdb.zip) |


## <a name="enthought-canopy"></a>Enthought Canopy

Enthought Canopy stellt Symbole für die zugehörigen Binärdateien ab Version 1.2 bereit. Die Symbole werden automatisch zusammen mit der Distribution installiert, Sie müssen jedoch den Ordner mit den Symbolen manuell zum Symbolpfad hinzufügen, wie oben beschrieben. In einer typischen Pro-Benutzer-Installation von Canopy befinden sich die Symbole für die 64-Bit-Version in `%UserProfile%\AppData\Local\Enthought\Canopy\User\Scripts` und für die 32-Bit-Version in `%UserProfile%\AppData\Local\Enthought\Canopy32\User\Scripts`.

Enthought Canopy 1.1 und früher sowie Enthought Python Distribution (EPD) stellen keine Interpretersymbole bereit und sind daher nicht mit dem Debuggen im gemischten Modus kompatibel.
