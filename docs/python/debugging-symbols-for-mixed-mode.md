---
title: "Symbole für das Debuggen im gemischten Modus mit Python Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
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
ms.sourcegitcommit: a42f5a30375192c89c9984e40ba0104da98d7253
ms.openlocfilehash: 9f7ba91262875344ded1e09277883abff292f359
ms.lasthandoff: 03/07/2017

---

# <a name="installing-debugging-symbols-for-python-interpreters"></a>Installieren von Debugsymbolen für Python-Interpreter

Um ein vollständiges Debuggen zu ermöglichen, muss der [Debugger für den gemischten Modus](debugging-mixed-mode.md) in Python Tools für Visual Studio (PTVS) zahlreiche interne Datenstrukturen im verwendeten Python-Interpreter analysieren. Dazu sind Debugsymbole für den Interpreter selbst erforderlich. Die entsprechende Symboldatei für „python27.dll“ beispielsweise ist „python27.pdb“.

Wenn PTVS erkennt, dass Symbole benötigt werden, werden Sie dazu aufgefordert, entweder einen Pfad zum Ordner mit Symboldateien anzugeben oder die Symbole herunterzuladen:

![Aufforderung zum Bereitstellen von Symbolen beim Debuggen im gemischten Modus](media/mixed-mode-debugging-symbols-required.png) 

Sie können Symboldateien aus der [offiziellen Distribution](#official-distribution) oder von [Enthought Canopy](#enthought-canopy) herunterladen, wie im Folgenden beschrieben. Wenn Sie die Python-Distribution eines Drittanbieters wie z.B. ActiveState Python verwenden, müssen Sie sich an die Autoren dieser Distribution wenden und sie um die Symbole bitten. (WinPython dagegen enthält den Python-Standardinterpreter in unveränderter Form, verwenden Sie dafür also die Symbole der offiziellen Distribution für die entsprechende Versionsnummer.)

Nachdem Sie die PDB-Dateien für Ihren Interpreter erhalten haben, stellen Sie diese auf folgende Weise für PTVS zur Verfügung, sodass sie zu Beginn einer Debugsitzung automatisch geladen werden:

1. Wählen Sie den Menübefehl **Tools > Optionen**, und navigieren Sie dann zu **Debuggen > Symbole**:

![Symboloptionen für den Debugger im gemischten Modus](media/mixed-mode-debugging-symbols.png)

1. Wählen Sie auf der Symbolleiste die Schaltfläche „Hinzufügen“ (im obigen Screenshot die zweite Schaltfläche von links, direkt neben dem Ausrufezeichen), navigieren Sie zum Ordner mit den PDB-Dateien, und wählen Sie **OK** aus.


## <a name="official-distribution"></a>Offizielle Distribution

In Python 3.5 und höher können Sie Debugsymbole über das Installationsprogramm einschließen (sowohl bei neuen als auch bei vorhandenen Installationen). Wählen Sie **Benutzerdefinierte Installation** und **Weiter**, um zu **Erweiterte Optionen** zu gelangen, und wählen Sie dann die Felder für **Debugsymbole herunterladen**und**Debugbinärdateien herunterladen**:

![Installationsprogramm für Python 3.x mit Debugsymbolen](media/mixed-mode-debugging-symbols-installer35.png)

Für Python 3.4.x und früher sind Symbole als herunterladbare ZIP-Dateien verfügbar. Extrahieren Sie diese Dateien nach dem Herunterladen in einen Ordner, und folgen Sie den Anweisungen im vorherigen Abschnitt, um sie bei PTVS zu registrieren.

| Python-Version | Downloads | 
| --- | --- | 
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
