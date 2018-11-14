---
title: Komponententests für Python
description: Einrichten von Komponententests für Python-Code in Visual Studio, um die Funktionen von Test-Explorer zum Ermitteln, Ausführen und Debuggen von Tests in vollem Umfang zu nutzen.
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
ms.openlocfilehash: e8a3a61b7c77031033c9cdc988753437f25166a1
ms.sourcegitcommit: 6a955a2d179cd0e137942389f940d9fcbbe125de
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 11/13/2018
ms.locfileid: "51607574"
---
# <a name="set-up-unit-testing-for-python-code"></a>Einrichten von Komponententests für Python-Code

Komponententests sind Codeelemente, die andere Codeeinheiten in einer Anwendung testen, in der Regel isolierte Funktionen, Klassen usw. Wenn eine Anwendung alle Unittests besteht, können Sie sich zumindest darauf verlassen, dass die Funktionalität im Detail korrekt ist.

In Python werden Komponententests ausgiebig zum Überprüfen von Szenarien beim Entwurf eines Programms verwendet. Die Python-Unterstützung in Visual Studio umfasst das Ermitteln, Ausführen und Debuggen von Unittests im Kontext Ihres Entwicklungsprozesses, sodass sie nicht separat ausgeführt werden müssen.

Dieser Artikel enthält eine kurze Übersicht über die Komponententestfunktionen in Visual Studio mit Python. Weitere Informationen zu Komponententests im Allgemeinen finden Sie unter [Komponententest für Code](../test/unit-test-your-code.md).

|   |   |
|---|---|
| ![Kamerasymbol für Video](../install/media/video-icon.png "Video ansehen") | [Sehen Sie sich ein Video (Microsoft Virtual Academy)](https://mva.microsoft.com/en-US/training-courses-embed/python-tools-for-visual-studio-2017-18121/Video-Testing-Python-hb46k6LWE_405918567) zu Komponententests in Python an (2 Minuten, 31 Sekunden). |

## <a name="discover-and-view-tests"></a>Entdecken und Anzeigen von Tests

Konventionell erkennt Visual Studio Tests als Methoden, deren Namen mit `test` beginnen. Um dieses Verhalten zu sehen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie ein in Visual Studio geladenes [Python-Projekt](managing-python-projects-in-visual-studio.md), klicken Sie mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Hinzufügen** > **Neues Element** und dann **Python-Komponententest**, gefolgt von **Hinzufügen**, aus.

1. Hierdurch wird eine Datei *test1.py* mit Code erstellt, der das `unittest`-Standardmodul importiert, eine Testklasse aus `unittest.TestCase` ableitet und `unittest.main()` aufruft, wenn Sie das Skript direkt ausführen:

    ```python
    import unittest

    class Test_test1(unittest.TestCase):
        def test_A(self):
            self.fail("Not implemented")

    if __name__ == '__main__':
        unittest.main()
    ```

1. Speichern Sie die Datei bei Bedarf, und öffnen Sie dann den **Test-Explorer** mit dem Menübefehl **Test** > **Windows** > **Test-Explorer**.

1. Der **Text-Explorer** durchsucht Ihr Projekt nach Tests und zeigt diese wie unten dargestellt an. Durch Doppelklicken auf einen Test wird dessen Quelldatei geöffnet.

    ![Test-Explorer mit Anzeige des Standardtests „test_A“](media/unit-test-A.png)

1. Wenn Sie Ihrem Projekt weitere Tests hinzufügen, können Sie die Ansicht im **Test-Explorer** über das Menü **Gruppieren nach** auf der Symbolleiste organisieren:

    ![Symbolleistenmenü „Gruppieren nach“ im Test-Explorer](media/unit-test-group-menu.png)

1. Sie können auch Text in das **Suchfeld** eingeben, um Tests nach Namen zu filtern.

Weitere Informationen zum `unittest`-Modul und zum Schreiben von Tests finden Sie in der [Python 2.7-Dokumentation](https://docs.python.org/2/library/unittest.html) bzw. in der [Python 3.4-Dokumentation](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="run-tests"></a>Tests durchführen

Im **Test-Explorer** können Sie Tests auf vielfältige Weise ausführen:

- **Alle ausführen** führt alle angezeigten Tests aus (gemäß Filter).
- Das Menü **Ausführen** stellt Ihnen Befehle zum Ausführen fehlerhafter, erfolgreicher oder nicht ausgeführter Tests als Gruppe zur Verfügung.
- Sie können einen oder mehrere Tests auswählen, mit der rechten Maustaste darauf klicken und **Ausgewählte Tests ausführen** wählen.

Tests werden im Hintergrund ausgeführt, und der **Test-Explorer** aktualisiert den Status der einzelnen Tests, sobald sie abgeschlossen sind:

- Erfolgreiche Tests werden mit einem grünen Häkchen markiert, und die zum Ausführen des Tests erforderliche Zeit wird angezeigt:

    ![Status „Erfolgreich“ für test_A](media/unit-test-A-pass.png)

- Fehlerhafte Tests werden mit einem roten Kreuz markiert und mit einem Link **Ausgabe** versehen, unter dem die Konsolenausgabe und die `unittest`-Ausgabe aus dem Testlauf angezeigt wird:

    ![Status „Fehlerhaft“ für test_A](media/unit-test-A-fail.png)

    ![Fehlerhafter test_A mit Grund](media/unit-test-A-fail-reason.png)

## <a name="debug-tests"></a>Debuggen von Tests

Da Unittests Codeteile sind, können sie genau wie jeder andere Code Fehler aufweisen und müssen gelegentlich in einem Debugger ausgeführt werden. Im Debugger können Sie Haltepunkte setzen, Variablen untersuchen und Code durchlaufen. Visual Studio bietet auch Diagnosetools für Unittests.

Um mit dem Debuggen zu beginnen, legen Sie einen anfänglichen Haltepunkt im Code fest, klicken Sie im **Test-Explorer** mit der rechten Maustaste auf den Test (oder eine Auswahl), und wählen Sie **Ausgewählte Tests debuggen** aus. Visual Studio startet den Python-Debugger auf dieselbe Weise wie für Anwendungscode.

![Debuggen eines Tests](media/unit-test-debugging.png)

Je nach Visual Studio-Version können Sie auch die Befehle **Code Coverage für ausgewählte Tests analysieren** und **Profiltest** verwenden. (Informationen finden Sie in der [Featurematrix](overview-of-python-tools-for-visual-studio.md#features-matrix).)

### <a name="known-issues"></a>Bekannte Probleme

- Beim Starten des Debugvorgangs scheint Visual Studio das Debuggen zu starten und zu beenden und dann erneut zu starten. Dies ist ein erwartetes Verhalten.
- Beim Debuggen mehrerer Tests wird jeder Test jeweils unabhängig durchgeführt, wodurch die Debugsitzung unterbrochen wird.
- Gelegentlich kann Visual Studio einen Test beim Debuggen nicht starten. In der Regel ist das erneute Debuggen des Tests erfolgreich.
- Beim Debuggen ist beim Test ein Rücksprung in die `unittest`-Implementierung möglich. Normalerweise wird der nächste Schritt bis zum Ende des Programms ausgeführt und das Debuggen beendet.
