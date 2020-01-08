---
title: Hinzufügen einer Schwellenwertregel für Auslastungstests
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- load tests, monitoring
- load tests, thresholds
- load tests, analyzing
- thresholds in load tests
ms.assetid: 3d8fac8f-426f-4155-9ced-f7cd4c79792c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d1389df0c307ad6ec65575fc7934e622928a0ca1
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591631"
---
# <a name="how-to-add-a-threshold-rule-using-the-load-test-editor"></a>Vorgehensweise: Hinzufügen einer Schwellenwertregel mithilfe des Auslastungstest-Editors

In Auslastungstests werden mithilfe von Schwellenwertregeln Leistungsindikatorwerte entweder mit einem konstanten Wert oder mit einem anderen Leistungsindikatorwert verglichen.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

## <a name="to-add-a-threshold-rule"></a>So fügen Sie eine Schwellenwertregel hinzu

1. Öffnen Sie einen Auslastungstest.

2. Erweitern Sie im Auslastungstest-Editor den Knoten **Indikatorensätze**.

3. Erweitern Sie in einem der Indikatorensätze eine der **Indikatorenkategorien**. Sie können z.B. **LoadTest:Scenario** auswählen. Erweitern Sie den Knoten.

4. Klicken Sie mit der rechten Maustaste auf einen der Indikatoren, z.B. **Benutzerauslastung** unter **LoadTest:Scenario**. Wählen Sie **Schwellenwertregel hinzufügen** aus.

     Das Dialogfeld **Schwellenwertregel hinzufügen** wird angezeigt.

5. Sie können sich zwischen den folgenden zwei Arten von Regeln entscheiden: **Mit Konstante vergleichen** oder **Compare Counter** (Mit Indikator vergleichen). Wählen Sie den gewünschten Typ, und legen Sie die Werte fest.

    > [!NOTE]
    > Legen Sie die **Warnung bei Überschreiten**-Eigenschaft auf **TRUE** fest, um anzugeben, dass das Überschreiten eines Schwellenwerts ein Problem darstellt, oder auf **FALSE** fest, um anzugeben, dass das Unterschreiten eines Schwellenwerts ein Problem darstellt.

## <a name="see-also"></a>Siehe auch

- [Analysieren von Verstößen gegen Schwellenwertregeln](../test/analyze-threshold-rule-violations-in-load-tests.md)
- [Festlegen von Indikatorensätzen und Schwellenwertregeln für Computer in einem Auslastungstest](../test/specify-counter-sets-and-threshold-rules-for-load-testing.md)
- [Analysieren von Auslastungstestergebnissen](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
