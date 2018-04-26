---
title: Konfigurieren der Codeanalyse in Visual Studio
ms.date: 04/04/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.propertypages.csvb
- vs.codeanalysis.propertypages.solution
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: afa7a75ae083133f2cff1197b2aa111a1d7bf719
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-code-analysis-for-a-managed-code-project"></a>Gewusst wie: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code

In Visual Studio können Sie aus einer Liste der Codeanalyse *-Regelsätze* um auf ein Projekt mit verwaltetem Code anzuwenden. Der Standardregelsatz sind *Microsoft-Mindestregeln*. Sie können einen anderen Regelsatz auf ein Projekt oder alle Projekte in einer Projektmappe anwenden.

> [!TIP]
> Informationen zum Konfigurieren eines Regelsatzes für ASP.NET-Webanwendungen finden Sie unter [Vorgehensweise: Konfigurieren der Codeanalyse für eine ASP.NET-Webanwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md).

## <a name="to-configure-a-rule-set-for-a-net-framework-project"></a>So konfigurieren Sie einen Regelsatz für ein .NET Framework-Projekt

1. Öffnen der **Codeanalyse** Registerkarte auf den Eigenschaftenseiten des Projekts. Sie können dies in einer der folgenden Methoden erfolgen:

   - In **Projektmappen-Explorer**, wählen Sie das Projekt. Wählen Sie auf der Menüleiste **analysieren** > **Konfigurieren der Codeanalyse** > **für \<Projektname >**.

   - Mit der rechten Maustaste des Projekts im **Projektmappen-Explorer** , und wählen Sie **Eigenschaften**, und wählen Sie dann die **Codeanalyse** Registerkarte.

1. In der **Konfiguration** und **Plattform** Listen, wählen Sie die Build-Konfiguration und die Zielplattform.

1. Wählen Sie zum Ausführen der Codeanalyse jedes Mal, wenn das Projekt erstellt wird, mit der ausgewählten Konfiguration der **Codeanalyse für Build aktivieren** Kontrollkästchen. Sie können Codeanalyse auch manuell ausführen, indem Sie auswählen **analysieren** > **Ausführen der Codeanalyse** > **Ausführen der Codeanalyse für \<Projektname >**.

1. Standardmäßig meldet die Codeanalyse keine Warnungen zu Code, der automatisch von Tools von Drittanbietern generiert wird. Um Warnungen zu generiertem Code anzuzeigen, deaktivieren Sie die **Ergebnisse aus generiertem Code unterdrücken** Kontrollkästchen.

    > [!NOTE]
    > Allerdings werden durch diese Option keine Codeanalysefehler und -warnungen zu generiertem Code unterdrückt, wenn die Fehler und Warnungen in Formularen und Vorlagen auftreten. Sie können sowohl anzeigen und verwalten den Quellcode für ein Formular oder eine Vorlage, ohne dabei überschrieben.

1. In der **diesen Regelsatz ausführen** führen Sie eines der folgenden:

    - Wählen Sie den Regelsatz, den Sie verwenden möchten.

    - Wählen Sie  **\<durchsuchen... >** finden Sie eine vorhandene benutzerdefinierte Regel festlegen, ist nicht in der Liste.

    - Definieren einer [benutzerdefinierten Regelsatz](../code-quality/how-to-create-a-custom-rule-set.md).

## <a name="specify-rule-sets-for-multiple-projects-in-a-solution"></a>Angeben von Regelsätzen für mehrere Projekte in einer Projektmappe

Standardmäßig werden alle verwalteten Projekte einer Projektmappe zugewiesen der *Microsoft-Mindestregeln* code Codeanalyse-Regelsatz. Sie können die Regelsätze, die den Projekten einer Projektmappe im zugewiesen sind ändern die **Eigenschaften** Dialogfeld für die Projektmappe.

1. Öffnen Sie die Lösung in Visual Studio.

2. Auf der **analysieren** klicken Sie im Menü **Codeanalyse für Projektmappe konfigurieren**.

3. Erweitern Sie ggf. **allgemeine Eigenschaften**, und wählen Sie dann **Codeanalyseeinstellungen**.

4. Sie können einen Regelsatz für ein oder mehrere Projekte angeben:

    - Wählen Sie den Projektnamen aus, um einen Regelsatz für ein einzelnes Projekt anzugeben.

    - Um einen Regelsatz für mehrere Projekte anzugeben, halten Sie **STRG** , und wählen Sie den Projektnamen.

    - Um alle Projekte in der Projektmappe angeben möchten, halten Sie **UMSCHALT** , und klicken Sie in der Projektliste auf.

5. Wählen Sie die **Regelsatz** Feld eines Projekts, und wählen Sie dann der Namen der Regel festlegen, dass Sie anwenden möchten.

## <a name="see-also"></a>Siehe auch

- [Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)