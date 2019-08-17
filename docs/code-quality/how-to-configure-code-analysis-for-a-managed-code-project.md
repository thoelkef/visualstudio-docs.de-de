---
title: Konfigurieren der Codeanalyse
ms.date: 04/04/2018
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a1b09b77eb051d32a3aabb929e9058786215cfb4
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551052"
---
# <a name="how-to-configure-legacy-analysis-for-managed-code"></a>Vorgehensweise: Legacy Analyse für verwalteten Code konfigurieren

In Visual Studio können Sie aus einer Liste von Code Analyse- [Regelsätzen](../code-quality/rule-set-reference.md) auswählen, die auf ein Projekt mit verwaltetem Code angewendet werden sollen. In der Standardeinstellung die **Microsoft-Mindestregeln** Regelsatz ausgewählt ist, aber Sie können bei Bedarf einen anderen Regelsatz anwenden. Regelsätze können auf eine oder mehrere Projekte in einer Projektmappe angewendet werden.

Informationen zum Konfigurieren eines Regelsatzes für ASP.NET-Webanwendungen finden [Sie unter Gewusst wie: Konfigurieren Sie die Code Analyse für eine ASP.net](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)-Webanwendung.

> [!NOTE]
> Dieser Artikel bezieht sich auf die Legacy Analyse und nicht auf [.NET Compiler Platform basierte Code](use-roslyn-analyzers.md)Analysetools, die nach dem erstellen keine Code Analyse ausführen.

## <a name="configure-a-rule-set-for-a-net-framework-project"></a>Konfigurieren eines Regelsatzes für ein .NET Framework Projekt

1. Öffnen der **Codeanalyse** Registerkarte auf den Eigenschaftenseiten des Projekts. Dies ist in einem der folgenden Arten möglich:

   - In **Projektmappen-Explorer**, wählen Sie das Projekt. Wählen Sie auf der Menüleiste **analysieren** > **Codeanalyse konfigurieren** > **für \<Projektname >** .

   - Mit der rechten Maustaste in des Projekts im **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**, und wählen Sie dann die **Codeanalyse** Registerkarte.

1. In der **Konfiguration** und **Plattform** Listen, wählen Sie die Buildplattform und die Zielplattform.

1. Codeanalyse ausführen jedes Mal, wenn das Projekt mit der ausgewählten Konfiguration erstellt wird, wählen die **Codeanalyse für Build aktivieren** Kontrollkästchen. Sie können die Codeanalyse auch manuell ausführen, indem Sie auswählen **analysieren** > **Codeanalyse ausführen** > **Ausführen der Codeanalyse für \<Projektname >** .

1. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Sie können sowohl anzeigen und verwalten den Quellcode für ein Formular oder einer Vorlage, ohne es überschrieben.

1. In der **diesen Regelsatz ausführen** aufzulisten, führen Sie eine der folgenden:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie  **\<durchsuchen... >** finden Sie eine vorhandene benutzerdefinierte Regel festlegen, ist nicht in der Liste.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Angeben von Regelsätzen für mehrere Projekte in einer Projektmappe

Standardmäßig werden alle verwalteten Projekten einer Projektmappe zugewiesen der *Microsoft-Mindestregeln* code Codeanalyse-Regelsatz. Sie können ändern, dass die Regelsätze, die den Projekten einer Projektmappe im zugewiesen sind, die **Eigenschaften** im Dialogfeld für die Lösung.

1. Öffnen Sie die Lösung in Visual Studio.

2. Auf der **analysieren** , wählen Sie im Menü **Codeanalyse für Projektmappe konfigurieren**.

3. Erweitern Sie ggf. **allgemeine Eigenschaften**, und wählen Sie dann **Codeanalyseeinstellungen**.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben:

    - Um einen Regelsatz für ein einzelnes Projekt anzugeben, wählen Sie den Namen des Projekts.

    - Um einen Regelsatz für mehrere Projekte angeben möchten, halten Sie die **STRG** , und wählen Sie den Projektnamen.

    - Um alle Projekte in der Projektmappe angeben möchten, halten Sie die **UMSCHALT** , und klicken Sie in der Projektliste.

5. Wählen Sie die **Regelsatz** Feld eines Projekts, und wählen Sie dann der Namen der Regel festlegen, dass Sie anwenden möchten.

## <a name="see-also"></a>Siehe auch

- [Codeanalyse-Regelsatzreferenz](../code-quality/rule-set-reference.md)
- [Vorgehensweise: Konfigurieren der Code Analyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)
