---
title: 'Tutorial: Arbeiten mit Python, Schritt 5: Installieren von Paketen'
description: Dies ist Schritt 5 einer grundlegenden Einführung in die Arbeit mit Python in Visual Studio, in dem die Features von Visual Studio zum Verwalten von Paketen in einer Python-Umgebung veranschaulicht werden.
ms.date: 03/05/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: tutorial
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: 18a4f274de38bab160144a9e13d6a6963168fff1
ms.sourcegitcommit: 33c954fbc8e05f7ba54bfa2c0d1bc1f9bbc68876
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/07/2018
---
# <a name="step-5-installing-packages-in-your-python-environment"></a>Schritt 5: Installieren von Paketen in Ihrer Python-Umgebung

**Vorheriger Schritt: [Ausführen von Code im Debugger](tutorial-working-with-python-in-visual-studio-step-04-debugging.md)**

Die Python-Entwicklercommunity hat Tausende von nützlichen Paketen erzeugt, die Sie in Ihre eigenen Projekte integrieren können. Visual Studio bietet eine Benutzeroberfläche für das Verwalten von Paketen in Ihren Python-Umgebungen.

1. Wählen Sie den Menübefehl **Ansicht > Weitere Fenster > Python-Umgebungen** aus. Das Fenster **Python-Umgebungen** wird als Peer für den Projektmappen-Explorer geöffnet und zeigt die verschiedenen Umgebungen an, die für Sie verfügbar sind. Die Liste enthält die Umgebungen, die Sie mithilfe des Visual Studio-Installers installiert haben und die, die Sie separat installiert haben. Die Umgebung in Fettdruck ist die Standardumgebung, die für neue Projekte verwendet wird.

  ![Fenster „Python-Umgebungen“](media/environments-default-view-blue.png)

1. Die Registerkarte **Übersicht** der Umgebung bietet schnellen Zugriff auf ein interaktives Fenster für diese Umgebung zusammen mit dem Installationsordner und den Interpretern der Umgebung. Klicken Sie beispielsweise auf **Interaktives Fenster öffnen**, und ein interaktives Fenster für diese bestimmte Umgebung wird in Visual Studio angezeigt.

1. Klicken Sie auf die Registerkarte **Pakete**, und Ihnen wird eine Liste der Pakete angezeigt, die derzeit in der Umgebung installiert sind.

  ![In einer Umgebung installierte Pakete](media/environments-installed-packages-blue.png)

1. Installieren Sie `matplotlib`, indem Sie den Namen in das Suchfeld eingeben und dann auf `pip install` klicken.

  ![Installieren von matplotlib in der Umgebung](media/environments-add-matplotlib1.png)

1. Stimmen Sie zu, wenn Sie zur Erhöhung der Rechte aufgefordert werden.

1. Nachdem das Paket installiert ist, wird es im Fenster der Python-Umgebung angezeigt. Über das **X** auf der rechten Seite des Pakets kann dieses deinstalliert werden.

  ![Abschließen der Installation von matplotlib in der Umgebung](media/environments-add-matplotlib2.png)

  Unterhalb der Umgebung wird möglicherweise eine kleine Statusanzeige eingeblendet, um darauf hinzuweisen, dass Visual Studio die IntelliSense-Datenbank für neu installierte Pakete erstellt. Die Registerkarte **IntelliSense** zeigt ausführlichere Informationen an. Beachten Sie, dass IntelliSense-Funktionen wie die automatische Vervollständigung und die Syntaxüberprüfung für dieses Paket nicht im Editor aktiv sind, bis die Datenbank vollständig erstellt ist.

  Beachten Sie, dass **Visual Studio 2017 Version 15.6** und höher eine andere und schnellere Methode für die Arbeit mit IntelliSense verwendet, und zeigen Sie eine diesbezügliche Meldung auf der **IntelliSense**-Registerkarte an.

1. Erstellen Sie ein Projekt, indem Sie auf **Datei > Neu > Projekt** klicken und die Vorlage „Python-Anwendung“ auswählen. Fügen Sie folgenden Code in die angezeigte Codedatei ein. Dadurch wird eine Kosinuswelle wie in den vorherigen Schritten des Tutorials erstellt, die dieses Mal jedoch grafisch dargestellt wird:

    ```python
    from math import radians
    import numpy as np     # installed with matplotlib
    import matplotlib.pyplot as plt

    def main():
        x = np.arange(0, radians(1800), radians(12))
        plt.plot(x, np.cos(x), 'b')
        plt.show()

    main()
    ```

1. Führen Sie das Programm mit (F5) oder ohne Debugger (STRG+F5) aus, um die Ausgabe anzuzeigen:

  ![Ausgabe des matplotlib-Beispiels](media/environments-add-matplotlib3.png)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Working with Git (Arbeiten mit Git)](tutorial-working-with-python-in-visual-studio-step-06-working-with-git.md)

### <a name="going-deeper"></a>Vertiefung

- [Python-Umgebungen](managing-python-environments-in-visual-studio.md)
