---
title: 'Gewusst wie: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Codeanalyse'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 339308675350bb6e4445b1dd068eb07d66f34164
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Vorgehensweise: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Analyse

Entwickler können das Tool Codemetrik zum Messen von Komplexität und verwaltbarkeit des Codes verwenden, aber Sie können keine Codemetrik aufrufen, als Teil einer in der Eincheckrichtlinie. Sie können allerdings Codeanalyseregeln, durch die überprüft die Kompatibilität des Codes mit Code Metriken Standards zu aktivieren und erzwingen Sie diese Regeln über Eincheckrichtlinien. Weitere Informationen zu Metriken für Code finden Sie unter [Code Metrikwerte](../code-quality/code-metrics-values.md).

Sie können die Vererbungstiefe, Klassenkopplung Wartbarkeitsindex und Komplexitätsregeln zum Erzwingen von wartbarem Code durch eine Eincheckrichtlinie für Codeanalyse aktivieren. Alle vier Regeln befinden sich unter der Kategorie "Verwaltbarkeit Regeln" in der Codeanalyse Gruppenrichtlinienverwaltungs-Editor.

Administratoren der Team Foundation-Versionskontrolle können Sie die Anforderungen in der Eincheckrichtlinie für Verwaltbarkeit Codeanalyseregeln hinzufügen. Diese einchecken, müssen Sie für Richtlinien Entwickler basierend auf diese regeländerungen vor dem Initiieren eines Eincheckvorgangs Codeanalyse ausgeführt.

## <a name="to-open-the-code-analysis-policy-editor"></a>Öffnen des Editors für die Codeanalyserichtlinie

1. In **Team Explorer**mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.

     Die **Quellcodeverwaltung** Dialogfeld wird angezeigt.

2. Auf der **Eincheckrichtlinie** Registerkarte, und klicken Sie auf **hinzufügen**.

     Die **hinzufügen in der Eincheckrichtlinie** Dialogfeld wird angezeigt.

3. In der **Eincheckrichtlinie** Liste der **Codeanalyse** Kontrollkästchen, und klicken Sie dann auf **OK**.

     Die **Code Analysis-Editor für Gruppenrichtlinien** Dialogfeld wird angezeigt.

## <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die Verwaltbarkeit von Codeanalyseregeln

1. In der **Code Analysis-Editor für Gruppenrichtlinien** Dialogfeld unter **Regeleinstellungen**, erweitern Sie die **Verwaltbarkeit Regeln** Knoten.

2. Wählen Sie die Kontrollkästchen für die folgenden Regeln:

    -   Die Tiefe der Vererbung: **CA1501 AvoidExcessiveInheritance** -Schwellenwert: Warnung bei einer Tiefe von mehr als 5 Ebenen

    -   Komplexität: **CA1502 AvoidExcessiveComplexity** -Schwellenwert: Warnung bei mehr als 25

    -   Wartbarkeitsindex: **CA1505 AvoidUnmaintainableCode** -Schwellenwert: Warnung bei weniger als 20

    -   Klassenkopplungen: **CA1506 AvoidExcessiveClassCoupling** -Schwellenwert: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode

    Wenn Sie einen Verstoß gegen eine Codeanalyseregel zu einen erfolgreichen Build verhindern möchten, wählen Sie außerdem, die **Warnung als ein Fehler behandeln** das Kontrollkästchen neben der Beschreibung der Regel.

3. Klicken Sie auf **OK**. Die neue Richtlinie gilt nun für Eincheckvorgängen.

## <a name="see-also"></a>Siehe auch

- [Codemetrikwerte](../code-quality/code-metrics-values.md)
- [Erstellen und Verwenden von Eincheckrichtlinien für die Analyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)