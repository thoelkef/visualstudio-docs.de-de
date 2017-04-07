---
title: IPython-REPL in Visual Studio | Microsoft-Dokumentation
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9bd06b0-2021-4e55-b933-8346476224a8
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
ms.sourcegitcommit: 7d726441c2d6953bd7b50451bec7fff05d5d71b0
ms.openlocfilehash: 9c0c0124ed508eff8621f946a40c0dda520bc05b
ms.lasthandoff: 03/10/2017

---

# <a name="using-python-in-the-interactive-window"></a>Verwenden von Python im interaktiven Fenster

Das interaktive Visual Studio-Fenster im IPython-Modus ist eine erweiterte, dennoch benutzerfreundliche interaktive Entwicklungsumgebung, die über Interactive Parallel Computing-Features verfügt. In diesem Thema behandeln wir die Verwendung von IPython im interaktiven Visual Studio-Fenster. Hierfür muss die [Anaconda](https://www.continuum.io)-Umgebung installiert sein, die IPython und die benötigten Bibliotheken enthält.

> [!Note]
> IronPython unterstützt IPython nicht, obwohl Sie es auf dem Formular „Interactive-Optionen“ auswählen können. Sie können für die [Funktionsanforderung](https://github.com/Microsoft/PTVS/issues/84) stimmen oder es bei Bedarf implementieren.

1. Stellen Sie sicher, dass das IPython-Paket ordnungsgemäß installiert ist, indem Sie in Ihrem Python-Installationsverzeichnis IPython im Pylab-Modus starten:

  ```bash
  ipython --pylab
  ```

1. Geben Sie Folgendes ein:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r')
  ```

1. Wenn alles richtig konfiguriert ist, sollte etwa Folgendes angezeigt werden:

    ![Ausgabe der IPython-Konfiguration ](media/ipython-repl-01.png)

1. Öffnen Sie Visual Studio, wechseln Sie zum Fenster der Python-Umgebungen (**Ansicht > Weitere Fenster > Python-Umgebungen**), und wählen Sie die Python-Umgebung.
1. Prüfen Sie, ob auf der **Pip**-Registerkarte `IPython` und `matplotlib` aufgelistet sind. Wenn dies nicht der Fall ist, installieren Sie sie hier.
1. Wählen Sie die Registerkarte **Übersicht**, wählen Sie **Interaktive Optionen konfigurieren**, legen Sie für **Interaktiver Modus** „IPython“ fest, und wählen Sie **OK**:

    ![Festlegen des interaktiven Modus auf IPython](media/ipython-repl-02.png)

1. Wählen Sie **Interaktives Fenster öffnen**, um das interaktive Fenster im IPython-Modus mit PyLab aufzurufen. Möglicherweise müssen Sie das Fenster zurücksetzen, wenn Sie gerade den interaktiven Modus geändert haben:

    ![Das interaktive Fenster im IPython-Modus](media/ipython-repl-03.png)

1. Geben Sie den folgenden Code ein:

  ```python
  x = linspace(0, 5, 10)
  y = x ** 2
  plot(x, y, 'r', x, x ** 3, 'g', x, x ** 4, 'b')
  ```

1. Nach Eingabe der letzten Zeile sollte ein Inlinediagramm angezeigt werden (dessen Größe Sie bei Bedarf ändern können, indem Sie an der unteren rechten Ecke ziehen).

    ![Inlinediagramm im interaktiven Fenster](media/ipython-repl-04.png)

1. Statt in REPL einzugeben, können Sie Code im Editor schreiben, ihn auswählen, mit der rechten Maustaste klicken und den Befehl **An Interactive senden** (STRG+E,E) wählen. Versuchen Sie, den folgenden Code in den Editor einzufügen, indem sie ihn mit STRG+A auswählen und dann an das interaktive Fenster senden. (Beachten Sie: Wenn Visual Studio Code an das interaktive Fenster sendet, wird er als Einheit gesendet, um zu vermeiden, dass Sie temporäre oder teilweise Diagramme erhalten.)

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
    
1. IPython verfügt über eine Reihe nützlicher Features, wie z.B. Escapevorgang zur Shell des Betriebssystems, Variablenersetzung, Ausgabenerfassung. Weitere Informationen finden Sie im IPython-Referenzhandbuch:

    ![Escapevorgang zur Shell des Betriebssystems](media/ipython-repl-06.png)

1. Sie können IPython auch im „Notebook“-Modus verwenden, wo Sie jeden beliebigen Browser unter einem beliebigen Betriebssystem als Canvas verwenden können. Das Back-End-IPython-Modul kann sich lokal auf Ihrem Computer oder einem Remotecomputer befinden. Azure bietet Unterstützung zur Ausführung von [IPython auf einer Windows- oder Linux-VM](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-linux-jupyter-notebook). In der [Azure-Notebooks-Vorschau](https://notebooks.azure.com) finden Sie auch kostenlose Jupyter Notebooks als Dienst in Azure:

    ![IPython-Notebook-Modus](media/ipython-repl-07.png)

