---
title: "Vorgehensweise: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Analyse | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code analysis, check-in policies
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: 80f3d2385fa1023637081b787c8d938ae42f79b4
ms.sourcegitcommit: d16c6812b114a8672a58ce78e6988b967498c747
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2018
---
# <a name="how-to-enforce-maintainable-code-with-a-code-analysis-check-in-policy"></a>Vorgehensweise: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie für die Analyse

Entwickler können das Tool Codemetrik zum Messen von Komplexität und verwaltbarkeit des Codes verwenden, aber Sie können keine Codemetrik aufrufen, als Teil einer in der Eincheckrichtlinie. Sie können allerdings Codeanalyseregeln, durch die überprüft die Kompatibilität des Codes mit Code Metriken Standards zu aktivieren und erzwingen Sie diese Regeln über Eincheckrichtlinien. Weitere Informationen zu Metriken für Code finden Sie unter [Code Metrikwerte](../code-quality/code-metrics-values.md).

Sie können die Vererbungstiefe, Klassenkopplung Wartbarkeitsindex und Komplexitätsregeln zum Erzwingen von wartbarem Code durch eine Eincheckrichtlinie für Codeanalyse aktivieren. Alle vier Regeln befinden sich unter der Kategorie "Verwaltbarkeit Regeln" in der Codeanalyse Gruppenrichtlinienverwaltungs-Editor.

Administratoren der Team Foundation-Versionskontrolle können Sie die Anforderungen in der Eincheckrichtlinie für Verwaltbarkeit Codeanalyseregeln hinzufügen. Diese einchecken, müssen Sie für Richtlinien Entwickler basierend auf diese regeländerungen vor dem Initiieren eines Eincheckvorgangs Codeanalyse ausgeführt.

## <a name="to-open-the-code-analysis-policy-editor"></a>Öffnen des Editors für die Codeanalyserichtlinie

1. in **Team Explorer**mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.

     The **Source Control** dialog box appears.

2. auf der **Eincheckrichtlinie** Registerkarte, und klicken Sie auf **hinzufügen**.

     The **Add Check-in Policy** dialog box appears.

3. in der **Eincheckrichtlinie** Liste der **Codeanalyse** Kontrollkästchen, und klicken Sie dann auf **OK**.

     The **Code Analysis Policy Editor** dialog box appears.

## <a name="to-enable-code-analysis-maintainability-rules"></a>So aktivieren Sie die Verwaltbarkeit von Codeanalyseregeln

1. in der **Code Analysis-Editor für Gruppenrichtlinien** Dialogfeld unter **Regeleinstellungen**, erweitern Sie die **Verwaltbarkeit Regeln** Knoten.

2. Wählen Sie 2. die Kontrollkästchen für die folgenden Regeln:

    -   Die Tiefe der Vererbung: **CA1501 AvoidExcessiveInheritance** -Schwellenwert: Warnung bei einer Tiefe von mehr als 5 Ebenen

    -   Komplexität: **CA1502 AvoidExcessiveComplexity** -Schwellenwert: Warnung bei mehr als 25

    -   Wartbarkeitsindex: **CA1505 AvoidUnmaintainableCode** -Schwellenwert: Warnung bei weniger als 20

    -   Klassenkopplungen: **CA1506 AvoidExcessiveClassCoupling** -Schwellenwert: Warnung bei mehr als 80 für eine Klasse und mehr als 30 für eine Methode

    Wenn Sie einen Verstoß gegen eine Codeanalyseregel zu einen erfolgreichen Build verhindern möchten, wählen Sie außerdem, die **Warnung als ein Fehler behandeln** das Kontrollkästchen neben der Beschreibung der Regel.

3. Klicken Sie auf **OK**. Die neue Richtlinie gilt nun für Eincheckvorgängen.

## <a name="see-also"></a>Siehe auch

[Code Metrikwerte](../code-quality/code-metrics-values.md)
[erstellen und Verwenden von Eincheckrichtlinien für die Analyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)