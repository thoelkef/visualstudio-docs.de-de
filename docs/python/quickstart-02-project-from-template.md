---
title: 'Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage in Visual Studio | Microsoft-Dokumentation'
ms.custom: 
ms.date: 09/25/2017
ms.reviewer: 
ms.suite: 
ms.technology: devlang-python
ms.devlang: python
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: kraigb
ms.author: kraigb
manager: ghogen
ms.workload: python
ms.openlocfilehash: ee329df0bda8869215969941024deba6d94743fe
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="quickstart-create-a-python-project-from-a-template-in-visual-studio"></a>Schnellstart: Erstellen eines Python-Projekts aus einer Vorlage in Visual Studio

Wenn Sie die [Python-Unterstützung in Visual Studio 2017 installiert haben](installation.md), können Sie ganz einfach ein neues Python-Projekt mithilfe einer Vielzahl von Vorlagen erstellen.

1. Starten Sie Visual Studio.

1. Klicken Sie auf **Datei > Neu > Projekt** (STRG+UMSCHALT+N). Suchen Sie im Dialogfeld **Neues Projekt** nach „Python“, und wählen Sie die gewünschte Vorlage aus. Daraufhin wird eine kurze Beschreibung des Vorlageninhalts angezeigt. Weitere Informationen finden Sie unter [Python-Projekte](python-projects.md#project-templates).

    ![Visual Studio 2017-Dialogfeld „Neues Projekt“ mit Python-Vorlage](media/projects-new-project-dialog2.png)

1. Wählen Sie für diesen Schnellstart die Vorlage „Python-Anwendung“ aus, benennen Sie das Projekt (z.B. „MakePI“), wählen Sie einen Speicherort aus, und klicken Sie auf **OK**. 

1. Visual Studio erstellt die Projektdatei (eine `.pyproj`-Datei auf einem Datenträger) wie von der Vorlage beschrieben zusammen mit allen anderen Dateien. Mit der Vorlage „Python-Anwendung“ enthält das Projekt nur eine leere Datei, die genauso heißt wie Ihr Projekt. Diese Datei ist im Visual Studio-Editor standardmäßig geöffnet.

    ![Das resultierende Projekt, wenn die Python-Anwendungsvorlage verwendet wird](media/projects-new-structure.png)

1. Fügen Sie in der geöffneten Datei Code hinzu, z.B. den unten aufgeführten. Mit diesem Code werden 999 Nachkommastellen von Pi berechnet und angezeigt:

    ```python
    """ Print digits of PI; code adapted from the second, shorter solution
    at http://www.codecodex.com/wiki/Calculate_digits_of_pi#Python
    """

    from time import perf_counter

    def pi_digits_Python(digits):
        scale = 10000
        maxarr = int((digits / 4) * 14)
        arrinit = 2000
        carry = 0
        arr = [arrinit] * (maxarr + 1)
        output = ""

        for i in range(maxarr, 1, -14):
            total = 0
            for j in range(i, 0, -1):
                total = (total * j) + (scale * arr[j])
                arr[j] = total % ((j * 2) - 1)
                total = total / ((j * 2) - 1)

            output += "%04d" % (carry + (total / scale))
            carry = total % scale

        return output;

    def test_py():
        digits = 1000;

        start = perf_counter()
        output = pi_digits_Python(digits);
        elapsed = perf_counter() - start;

        print("PI to " + str(digits) + " digits in " + str(int(elapsed * 10000)/10000) + " seconds:")

        ## replace inserts the decimal point
        print(output.replace("3", "3.", 1))

    if __name__ == "__main__":
        test_py();
    ```

1. Drücken Sie „STRG+F5“, oder klicken Sie im Menü auf **Debuggen > Ohne Debuggen starten**, und führen Sie das Programm aus. Die Ergebnisse werden in einem Konsolenfenster angezeigt.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Tutorial: Arbeiten mit Python in Visual Studio](vs-tutorial-01-01.md)

## <a name="see-also"></a>Siehe auch

- [Erstellen einer Umgebung für einen vorhandenen Python-Interpreter](python-environments.md#creating-an-environment-for-an-existing-interpreter)
- [Installieren der Python-Unterstützung für Visual Studio 2015 und früher](installation.md)
- [Installationsspeicherorte](installation.md#install-locations)
