---
title: 'Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: e8c63e7b54f1303f62fca938cb5dc44147af88dd
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53883242"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-an-azure-devops-project-check-in-policy"></a>Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit einer Eincheckrichtlinie für Azure DevOps-Projekt

Synchronisieren Sie die codeanalyseeinstellungen für Codeprojekte der Eincheckrichtlinie für das Azure DevOps-Projekt durch Angabe eines Regelsatzes, das mindestens die Regeln enthält, die in der Regel legen Sie für den Check-in-Richtlinie angegeben werden. Der leitende Entwickler können Sie mit dem Namen und Speicherort der Regel legen Sie für den Check-in-Richtlinie informieren. Sie können eine der folgenden Optionen verwenden, um sicherzustellen, dass die Codeanalyse für das Projekt den richtigen Satz an Regeln verwendet:

-   Wenn eine der integrierten Regelsätzen Microsoft die Check-in-Richtlinie verwendet wird, öffnen Sie das Dialogfeld "Eigenschaften" für das Codeprojekt, zeigt die Codeanalyse-Seite und wählen Sie die Regel, die auf der Seite "Codeanalyse" von den projekteinstellungen Code festgelegt. Die Microsoft-Standardregelsätze automatisch mit Visual Studio installiert werden auf schreibgeschützt festgelegt werden und sollte nicht bearbeitet werden. Wenn die Regelsätze nicht bearbeitet werden, garantiert die Regeln in der Richtlinie und eine Regel für das lokale Gruppen entsprechen.

-   Wenn die Eincheckrichtlinie ein benutzerdefinierten Regelsatzes verwendet wird, führen Sie einen Get-Vorgang für die Regelsatzdatei in der Versionskontrolle, um eine lokale Kopie zu erstellen. Geben Sie dann diesen lokalen Speicherort in den Code Analysis-Einstellungen für das Codeprojekt ein. Die Regeln werden garantiert, wenn die Regel legen Sie für den Check-in-Richtlinie auf dem neuesten Stand ist.

     Wenn Sie den Speicherort der Versionskontrolle in einen lokalen Ordner, die in der gleichen Beziehung in das Stammverzeichnis des Azure DevOps-Projekt wie Ihr Codeprojekt ist zuordnen, wird der Speicherort der Regel mithilfe eines relativen Pfads festgelegt. Der relative Pfad wird sichergestellt, dass die Einstellung des Code-Projekt für die Codeanalyse auf andere Computer verschoben werden kann.

-   Passen Sie eine Kopie der Regel legen Sie für die Eincheckrichtlinie für ein Codeprojekt. Stellen Sie sicher, dass der neue Regelsatz enthält alle Regeln in der Check-in-Richtlinie und alle anderen Regeln, die Sie einschließen möchten. Sie müssen sicherstellen, werden, dass der Regelsatz alle Regeln in der Regel legen Sie für den Check-in-Richtlinie enthält.

## <a name="to-specify-a-microsoft-standard-rule-set"></a>Geben Sie einen Microsoft-standard-Regelsatz fest

1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.

2.  Klicken Sie auf **Codeanalyse**.

3.  In der **diesen Regelsatz ausführen** Liste, klicken Sie auf der Eincheckrichtlinie-Regelsatz.

## <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Angeben einen benutzerdefinierte Eincheckrichtlinie-Regelsatz

1.  Führen Sie bei Bedarf einen Get-Vorgang für die Regelsatzdatei an, die angibt, der Eincheckrichtlinie.

2.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.

3.  Klicken Sie auf **Codeanalyse**.

4.  In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.

5.  In der **öffnen** Dialogfeld geben die Eincheckrichtlinie Regelsatz Datei.

## <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Legen zum Erstellen einer benutzerdefinierten Regel für ein Codeprojekt

1.  Führen Sie eines der Verfahren in diesem Thema die Check-in-Richtlinie des Azure DevOps-Projekts auf der Seite "Codeanalyse" im Dialogfeld Projekt Einstellungen auswählen.

2.  Klicken Sie auf **Öffnen**.

3.  Hinzufügen oder Entfernen von Regeln mithilfe der [Regelsatz-Editor](../code-quality/working-in-the-code-analysis-rule-set-editor.md).

4.  Speichern Sie den geänderten Regelsatz, um eine RULESET-Datei auf dem lokalen Computer oder einen UNC-Pfad.

5.  Öffnen Sie das Dialogfeld "Eigenschaften" für das Codeprojekt, und zeigen die **Codeanalyse** Seite.

6.  In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.

7.  In der **öffnen** Dialogfeld geben den Regelsatz-Datei.