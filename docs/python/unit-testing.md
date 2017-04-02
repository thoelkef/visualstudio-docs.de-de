---
title: "Komponententests in Python Tools für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 3/7/2017
ms.prod: visual-studio-dev15
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-python
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f3ad6523-5a4e-4209-8977-adc2da305df2
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
ms.openlocfilehash: f1148cb9e4d50241580190f274d6a4c2e3979b80
ms.lasthandoff: 03/10/2017

---

# <a name="setting-up-unit-testing-for-python-code"></a>Einrichten von Komponententests für Python-Code

Komponententests sind Codeelemente, die andere Codeeinheiten in einer Anwendung testen, in der Regel isolierte Funktionen, Klassen usw. Wenn eine Anwendung alle Komponententests besteht, können Sie sich zumindest darauf verlassen, dass die Funktionalität im Detail korrekt ist.

In Python werden Komponententests ausgiebig zum Überprüfen von Szenarien beim Entwurf eines Programms verwendet. Python-Tools für Visual Studio (PTVS) bietet Unterstützung für das Ermitteln, Ausführen und Debuggen von Komponententests im Kontext Ihres Entwicklungsprozesses, sodass sie nicht separat ausgeführt werden müssen.

Dieses Thema enthält eine kurze Übersicht über die Komponententestfunktionen in Visual Studio mit Python. Weitere Informationen zu Komponententests im Allgemeinen finden Sie unter [Komponententest für Code](../test/unit-test-your-code.md).

## <a name="discovering-and-viewing-tests"></a>Ermitteln und Anzeigen von Tests

Gemäß der Konvention erkennt PTVS Tests als Methoden, deren Namen mit „Test“ beginnen. Um dies zu untersuchen, führen Sie die folgenden Schritte aus:

1. Öffnen Sie ein in Visual Studio geladenes [Python-Projekt](python-projects.md), klicken Sie mit der rechten Maustaste auf Ihr Projekt, wählen Sie **Hinzufügen > Neues Element**, und wählen Sie dann **Python-Komponententest**, gefolgt von **Hinzufügen**.

1. Hierdurch wird eine Datei „test1.py“ mit Code erstellt, der das `unittest`-Standardmodul importiert, eine Testklasse aus `unittest.TestCase` ableitet und `unittest.main()` aufruft, wenn Sie das Skript direkt ausführen:

  ```python
  import unittest

  class Test_test1(unittest.TestCase):
      def test_A(self):
          self.fail("Not implemented")

  if __name__ == '__main__':
      unittest.main()
  ```

1. Speichern Sie die Datei bei Bedarf, und öffnen Sie dann den Test-Explorer mit dem Menübefehl **Test > Windows > Test-Explorer**.

1. Der Test-Explorer durchsucht Ihr Projekt auf Tests und zeigt diese wie unten dargestellt an. Durch Doppelklicken auf einen Test wird dessen Quelldatei geöffnet.

    ![Test-Explorer mit Anzeige des Standardtests „test_A“](media/unit-test-A.png)

1. Wenn Sie Ihrem Projekt weitere Tests hinzufügen, können Sie die Ansicht im Test-Explorer über das Menü „Gruppieren nach“ auf der Symbolleiste organisieren:

    ![Symbolleistenmenü „Gruppieren nach“ im Test-Explorer](media/unit-test-group-menu.png)

1. Sie können auch Text in das Suchfeld eingeben, um Tests nach Namen zu filtern.

Weitere Informationen zum `unittest`-Modul und zum Schreiben von Tests finden Sie in der [Python 2.7-Dokumentation](https://docs.python.org/2/library/unittest.html) bzw. in der [Python 3.4-Dokumentation](https://docs.python.org/3/library/unittest.html) (python.org).

## <a name="running-tests"></a>Ausführen von Tests

Im Test-Explorer können Sie Tests auf vielfältige Weise ausführen:

- **Alle ausführen** führt alle angezeigten Tests aus (gemäß Filter).
- Das Menü **Ausführen** stellt Ihnen Befehle zum Ausführen fehlerhafter, erfolgreicher oder nicht ausgeführter Tests als Gruppe zur Verfügung.
- Sie können einen oder mehrere Tests auswählen, mit der rechten Maustaste darauf klicken und **Ausgewählte Tests ausführen** wählen.

Tests werden im Hintergrund ausgeführt, und der Test-Explorer aktualisiert den Status der einzelnen Tests, sobald sie abgeschlossen sind:

- Erfolgreiche Tests werden mit einem grünen Häkchen markiert, und die zum Ausführen des Tests erforderliche Zeit wird angezeigt:

    ![Status „Erfolgreich“ für test_A](media/unit-test-A-pass.png)

- Fehlerhafte Tests werden mit einem roten Kreuz markiert und mit einem Link **Ausgabe** versehen, unter dem die Konsolenausgabe und die `unittest`-Ausgabe aus dem Testlauf angezeigt wird:

    ![Status „Fehlerhaft“ für test_A](media/unit-test-A-fail.png)

    ![Fehlerhafter test_A mit Grund](media/unit-test-A-fail-reason.png)

## <a name="debugging-tests"></a>Debuggen von Tests

Da Komponententests Codeteile sind, können sie genau wie jeder andere Code Fehler aufweisen und müssen gelegentlich in einem Debugger ausgeführt werden, in dem Sie Breakpoints festlegen, Variablen untersuchen und den Code schrittweise durchlaufen können. PTVS bietet auch Diagnosetools

Um mit dem Debuggen zu beginnen, legen Sie einen anfänglichen Haltepunkt im Code fest, klicken Sie im Test-Explorer mit der rechten Maustaste auf den Test (oder eine Auswahl), und wählen Sie **Ausgewählte Tests debuggen**. Visual Studio startet den Python-Debugger auf dieselbe Weise wie für Anwendungscode.

![Debuggen eines Tests](media/unit-test-debugging.png)

Je nach PTVS-Version können Sie auch die Befehle **Code Coverage für ausgewählte Tests analysieren** und **Profiltest** verwenden. (Informationen finden Sie in der [Featurematrix](python-in-visual-studio.md#features-matrix).)

### <a name="known-issues"></a>Bekannte Probleme

- Beim Starten des Debugvorgangs scheint Visual Studio das Debuggen zu starten und zu beenden und dann erneut zu starten. Dabei handelt es sich um das erwartete Verhalten.
- Beim Debuggen mehrerer Tests wird jeder Test jeweils unabhängig durchgeführt, wodurch die Debugsitzung unterbrochen wird.
- Gelegentlich kann Visual Studio einen Test beim Debuggen nicht starten. In der Regel führt der erneute Versuch zum Debuggen des Tests zum Erfolg.
- Beim Debuggen ist beim Test ein Rücksprung in die `unittest`-Implementierung möglich. Normalerweise wird der nächste Schritt bis zum Ende des Programms ausgeführt und das Debuggen beendet.
