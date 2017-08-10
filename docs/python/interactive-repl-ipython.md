---
title: IPython-REPL in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 7/13/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
caps.latest.revision: 1
author: kraigb
ms.author: kraigb
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6d25db4639f2c8391c1e32542701ea359f560178
ms.openlocfilehash: 9553aa4944f652c7b8505b0d99d5c2b88167f872
ms.contentlocale: de-de
ms.lasthandoff: 07/18/2017

---

# <a name="using-ipython-in-the-interactive-window"></a>Verwenden von IPython im interaktiven Fenster

Das interaktive Visual Studio-Fenster im IPython-Modus ist eine erweiterte, dennoch benutzerfreundliche interaktive Entwicklungsumgebung, die über Interactive Parallel Computing-Features verfügt. Dieses Thema führt Sie durch die Verwendung von IPython im interaktiven Visual Studio-Fenster. In diesem sind alle regulären Funktionen von [interactive windows (interaktiven Fenster)](interactive-repl.md) ebenfalls verfügbar.

Für diese exemplarische Vorgehensweise muss die [Anaconda](https://www.continuum.io)-Umgebung installiert sein, die IPython und die benötigten Bibliotheken enthält.

> [!Note]
> IronPython unterstützt IPython nicht, obwohl Sie es auf dem Formular „Interactive-Optionen“ auswählen können. Weitere Informationen finden Sie unter [feature request](https://github.com/Microsoft/PTVS/issues/84) (Funktionsanforderungen).

1. Öffnen Sie Visual Studio, wechseln Sie zum Fenster der Python-Umgebungen (**Ansicht > Weitere Fenster > Python-Umgebungen**), und wählen Sie die Python-Umgebung, die beim Starten von IPython angezeigt wurde.

1. Sehen sie sich die Registerkarte **Packages** (Pakete) (oder **pip**) an und stellen Sie sicher, dass `IPython` und `matplotlib` aufgeführt sind. Wenn dies nicht der Fall ist, installieren Sie sie hier.

1. Wählen Sie die Registerkarte **Overview** (Übersicht) und klicken Sie auf **Use IPython interactive mode** (Interaktiven IPython-Modus verwenden). (In Visual Studio 2015 klicken Sie auf **Configure interactive options** (Interaktive Optionen konfigurieren), um den Dialog **Optionen** zu öffnen, setzen den **Interactive Mode** (Interaktiven Modus) auf IPython, und klicken dann auf **OK**).    

1. Wählen Sie **Open interactive window** (Interaktives Fenster öffnen), um das interaktive Fenster im IPython-Modus aufzurufen. Sie müssen das Fenster eventuell zurücksetzen, wenn Sie gerade den interaktiven Modus geändert haben. Gegebenenfalls müssen Sie die EINGABETASTE drücken, wenn lediglich eine >>>-Eingabeaufforderung angezeigt wird.

    ![Das interaktive Fenster im IPython-Modus](media/ipython-repl-03.png)

1. Geben Sie den folgenden Code ein:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Nach Eingabe der letzten Zeile sollte ein Inlinediagramm angezeigt werden (dessen Größe Sie bei Bedarf ändern können, indem Sie an der unteren rechten Ecke ziehen).

    ![Inlinediagramm im interaktiven Fenster](media/ipython-repl-04.png)

1. Statt in REPL einzugeben, können Sie Code im Editor schreiben, ihn auswählen, mit der rechten Maustaste klicken und den Befehl **Send to interactive** (An Interactive senden) wählen ( oder STRG+EINGABETASTE drücken). Versuchen Sie, den folgenden Code in eine neue Datei im Editor einzufügen, indem sie ihn mit STRG+A auswählen und dann an das interaktive Fenster senden. (Beachten Sie: Visual Studio sendet den Code als Einheit, um zu vermeiden, dass Sie temporäre oder teilweise Diagramme erhalten. Beachten Sie auch, dass Visual Studio ein interaktives Fenster für die Umgebung öffnet, die im **Python Environments** (Python-Umgebungen)-Fenster als Standardeinstellung festgelegt ist, wenn Sie gerade kein Python-Projekt mit einer anderen Umgebung geöffnet haben.

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
        # the first bar of each set will be colored cyan.
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

## <a name="related-topics"></a>Verwandte Themen

- Wenn Sie Jupyter einfach und ohne Installation verwenden möchten, testen Sie den [Azure Notebooks hosted service (gehosteten Azure-Dienst für Notebooks)](https://notebooks.azure.com/), um Ihre Notebooks zu verwalten und mit anderen zu teilen.

- Sie können Jupyter (ehemals IPython) auch auf Ihrem eigenen virtuellen Computer (Windows oder Linux) auf Azure ausführen. Weitere Informationen finden Sie unter [Creating an Azure VM. installing Jupyter, and running Jupyter Notebook on Azure (Erstellen einer Azure-VM, Installieren von Jupyter und Ausführen von Jupyter-Notebook in Azure)](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook).

