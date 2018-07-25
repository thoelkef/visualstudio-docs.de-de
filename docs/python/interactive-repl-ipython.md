---
title: IPython REPL (Interaktives Fenster)
description: Verwenden des interaktiven Visual Studio-Fensters im IPython-Modus als benutzerfreundliche interaktive Entwicklungsumgebung mit Funktionen für interaktives paralleles Computing.
ms.date: 06/19/2018
ms.prod: visual-studio-dev15
ms.technology: vs-python
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- python
- data-science
ms.openlocfilehash: adfd037cc7362a4aa088d57c3776379caf6de5e3
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057660"
---
# <a name="using-ipython-in-the-interactive-window"></a>Verwenden von IPython im interaktiven Fenster

Das interaktive Visual Studio-Fenster im IPython-Modus ist eine erweiterte, dennoch benutzerfreundliche interaktive Entwicklungsumgebung, die über Interactive Parallel Computing-Features verfügt. Dieser Artikel führt Sie durch die Verwendung von IPython im interaktiven Visual Studio-Fenster. In diesem sind alle regulären Funktionen des [interaktiven Fensters](python-interactive-repl-in-visual-studio.md) ebenfalls verfügbar.

Für diese exemplarische Vorgehensweise muss die [Anaconda](https://www.continuum.io)-Umgebung installiert sein, die IPython und die benötigten Bibliotheken enthält.

> [!Note]
> IronPython unterstützt IPython nicht, obwohl Sie es auf dem Formular „Interactive-Optionen“ auswählen können. Weitere Informationen finden Sie unter [feature request](https://github.com/Microsoft/PTVS/issues/84) (Funktionsanforderungen).

1. Öffnen Sie Visual Studio, wechseln Sie zum Fenster der Python-Umgebungen (**Ansicht > Weitere Fenster > Python-Umgebungen**), und wählen Sie eine Anaconda-Umgebung aus.

1. Überprüfen Sie die Registerkarte **Pakete (Conda)** (die als **pip** oder **Pakete** angezeigt werden kann) für diese Umgebung, um sicherzustellen, dass `ipython` und `matplotlib` aufgeführt sind. Wenn dies nicht der Fall ist, installieren Sie sie hier. Weitere Informationen finden Sie unter [Referenz zu den Registerkarten im Fenster „Python-Umgebungen“](python-environments-window-tab-reference.md).

1. Wählen Sie die Registerkarte **Overview** (Übersicht) und klicken Sie auf **Use IPython interactive mode** (Interaktiven IPython-Modus verwenden). (In Visual Studio 2015 klicken Sie auf **Configure interactive options** (Interaktive Optionen konfigurieren), um den Dialog **Optionen** zu öffnen, setzen den **Interactive Mode** (Interaktiven Modus) auf IPython, und klicken dann auf **OK**).

1. Wählen Sie **Open interactive window** (Interaktives Fenster öffnen), um das interaktive Fenster im IPython-Modus aufzurufen. Sie müssen das Fenster eventuell zurücksetzen, wenn Sie gerade den interaktiven Modus geändert haben. Gegebenenfalls müssen Sie die EINGABETASTE drücken, wenn nur eine >>>-Eingabeaufforderung angezeigt wird, damit eine Eingabeaufforderung wie „In [2]“ angezeigt wird.

    ![Das interaktive Fenster im IPython-Modus](media/ipython-repl-03.png)

1. Geben Sie den folgenden Code ein:

  ```python
  import matplotlib.pyplot as plt
  import numpy as np
  
  x = np.linspace(0, 5, 10)
  y = x ** 2
  plt.plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Nach Eingabe der letzten Zeile sollte ein Inlinediagramm angezeigt werden (dessen Größe Sie bei Bedarf ändern können, indem Sie an der unteren rechten Ecke ziehen).

    ![Inlinediagramm im interaktiven Fenster](media/ipython-repl-04.png)

1. Statt den Code in die REPL einzugeben, können Sie ihn im Editor schreiben, ihn auswählen, mit der rechten Maustaste klicken und den Befehl **An interaktives Fenster senden** auswählen (oder STRG+EINGABETASTE drücken). Versuchen Sie, den folgenden Code in eine neue Datei im Editor einzufügen, indem sie ihn mit STRG+A auswählen und dann an das interaktive Fenster senden. (Visual Studio sendet den Code als Einheit, um zu vermeiden, dass Sie temporäre oder unvollständige Diagramme erhalten. Visual Studio öffnet ein interaktives Fenster für die Umgebung, die im Fenster **Python-Umgebungen** als Standardeinstellung festgelegt ist, wenn Sie gerade kein Python-Projekt mit einer anderen Umgebung geöffnet haben.)

    ```python
    from mpl_toolkits.mplot3d import Axes3D
    import matplotlib.pyplot as plt
    import numpy as np
    fig = plt.figure()
    ax = fig.add_subplot(111, projection='3d')
    for c, z in zip(['r', 'g', 'b', 'y'], [30, 20, 10, 0]):
        xs = np.arange(20)
        ys = np.random.rand(20)
        # You can provide either a single color or an array. To demonstrate this,
        # the first bar of each set is colored cyan.
        cs = [c] * len(xs)
        cs[0] = 'c'
        ax.bar(xs, ys, zs=z, zdir='y', color=cs, alpha=0.8)

    ax.set_xlabel('X')
    ax.set_ylabel('Y')
    ax.set_zlabel('Z')
    plt.show()
    ```

    ![Senden von Code aus dem Editor an das interaktive Fenster](media/ipython-repl-05.png)

1. Um die Diagramme außerhalb des interaktiven Fensters anzuzeigen, führen Sie den Code stattdessen mit dem Befehl **Debuggen > Starten ohne Debugging** aus.

IPython verfügt über viele weitere nützliche Features, wie z.B. Escapevorgang zur Shell des Betriebssystems, Variablenersetzung, Ausgabenerfassung usw. Weitere Informationen finden Sie in der [IPython documentation (IPython Dokumentation)](http://ipython.org/documentation.html).

## <a name="related-articles"></a>Verwandte Artikel

- Wenn Sie Jupyter einfach und ohne Installation verwenden möchten, testen Sie den [Azure Notebooks hosted service (gehosteten Azure-Dienst für Notebooks)](https://notebooks.azure.com/), um Ihre Notebooks zu verwalten und mit anderen zu teilen.

- Sie können Jupyter (ehemals IPython) auch auf Ihrem eigenen virtuellen Computer (Windows oder Linux) auf Azure ausführen. Weitere Informationen finden Sie unter [Creating an Azure VM. installing Jupyter, and running Jupyter Notebook on Azure (Erstellen einer Azure-VM, Installieren von Jupyter und Ausführen von Jupyter-Notebook in Azure)](/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).
