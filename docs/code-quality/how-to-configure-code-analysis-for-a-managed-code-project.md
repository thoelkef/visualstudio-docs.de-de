---
title: 'Vorgehensweise: Konfigurieren der Codeanalyse für ein Projekt mit verwaltetem Code | Microsoft Docs'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: article
f1_keywords:
- vs.codeanalysis.propertypages.csvb
helpviewer_keywords:
- code analysis, selecting rule sets
- code analysis, rule sets
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- dotnet
ms.openlocfilehash: 46d41b09f0f6639195613c8a4d9a08f952c79525
ms.sourcegitcommit: efd8c8e0a9ba515d47efcc7bd370eaaf4771b5bb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2018
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

    - Definieren Sie einen benutzerdefinierten Regelsatz. Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).

## <a name="see-also"></a>Siehe auch

- [Exemplarische Vorgehensweise: Konfigurieren und Verwenden eines benutzerdefinierten Regelsatzes](../code-quality/walkthrough-configuring-and-using-a-custom-rule-set.md)
- [Gewusst wie: Konfigurieren der Codeanalyse für eine ASP.NET-Anwendung](../code-quality/how-to-configure-code-analysis-for-an-aspnet-web-application.md)