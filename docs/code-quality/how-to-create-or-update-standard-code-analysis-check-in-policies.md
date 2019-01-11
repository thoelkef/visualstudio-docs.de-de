---
title: Erstellen oder Aktualisieren von Standardeincheckrichtlinien Codeanalyse-Eincheckrichtlinien
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.policyeditor
helpviewer_keywords:
- code analysis, migrating check-in policy
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 22a74926f4fd9136e15757eb6967d5eb56a8ecbf
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53890338"
---
# <a name="how-to-create-or-update-standard-code-analysis-check-in-policies"></a>Vorgehensweise: Erstellen oder Aktualisieren von Standardeincheckrichtlinien Codeanalyse-Eincheckrichtlinien

Sie können anfordern, dass die Codeanalyse auf alle Codeprojekte in einem Azure DevOps-Projekt ausgeführt werden, mit der Eincheckrichtlinie für die Analyse. Codeanalyse erfordert, kann die Qualität des Codes verbessern, die in die CodeBase überprüft wird.

> [!NOTE]
> Dieses Feature ist nur verfügbar, wenn Sie Team Foundation Server verwenden.

Eincheckrichtlinien für die Analyse in den projekteinstellungen festgelegt werden und gelten für jedes Codeprojekt. Codeanalysen werden bei Projekten mit Code in der Projektdatei (XXPROJ) für das Codeprojekt konfiguriert. Codeanalysen werden auf dem lokalen Computer ausgeführt. Wenn Sie eine Eincheckrichtlinie für die Analyse ermöglichen, Dateien in einem Codeprojekt, die eingecheckt werden, nach ihrer letzten Bearbeitung kompiliert werden müssen und eine Codeanalyse ausgeführt werden, mindestens enthält müssen die Regeln in den projekteinstellungen auf dem Computer ausgeführt werden, in dem die Änderung s vorgenommen wurden.

- Für verwalteten Code, Festlegen der Check-in-Richtlinie durch Angabe einer *Regelsatz* , enthält eine Teilmenge der Regeln für die Codeanalyse.

- Für C/C++-Code in Visual Studio 2017 Version 15.6 und früher erfordert die Check-in-Richtlinie an, dass alle Regeln für die Codeanalyse ausgeführt werden. Sie können die präprozessoranweisungen deaktivieren bestimmte Regeln für die einzelne Codeprojekte in Ihrem Azure DevOps-Projekt hinzufügen. In 15.7 und höher können Sie **/ analyze: Ruleset** an welche Regeln ausgeführt. Weitere Informationen finden Sie unter [Verwenden von Regelsätzen zum Festlegen von C++-Regeln für die Ausführung](using-rule-sets-to-specify-the-cpp-rules-to-run.md).

Nachdem Sie eine Eincheckrichtlinie für verwalteten Code angegeben haben, können Teammitglieder ihre codeanalyseeinstellungen für Codeprojekte an den Richtlinieneinstellungen für Azure DevOps-Projekt synchronisieren.

## <a name="to-open-the-check-in-policy-editor"></a>Die Check-in Gruppenrichtlinienverwaltungs-Editor öffnen

1. In Team Explorer mit der Maustaste des Projektnamens, zeigen Sie auf **Projekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.

1. In der **Quellcodeverwaltung** wählen Sie im Dialogfeld die **Eincheckrichtlinie** Registerkarte.

1. Führen Sie einen der folgenden Schritte aus:

    - Klicken Sie auf **hinzufügen** zum Erstellen einer neuen Check-in-Richtlinie.

    - Doppelklicken Sie auf die vorhandene **Codeanalyse** Element in der **Richtlinientyp** Liste, um die Richtlinie zu ändern.

## <a name="to-set-policy-options"></a>Festlegen von Optionen

Aktivieren Sie oder deaktivieren Sie die folgenden Optionen:

|Option|Beschreibung|
|------------|-----------------|
|**Erzwingen Sie, um nur die Dateien enthalten, die Teil der aktuellen Projektmappe eingecheckt.**|Codeanalyse kann nur auf Dateien in Projektmappen und Projektdateien Konfigurationsdateien angegeben ausgeführt. Diese Richtlinie wird sichergestellt, dass sämtlicher Code, der Teil einer Projektmappe wird analysiert wird.|
|**C/C++-Codeanalyse erzwingen (/ analyze)**|Erfordert, dass alle C- oder C++-Projekte erstellt werden, mit dem / analyze-Compileroption, um die Codeanalyse ausgeführt wird, bevor sie eingecheckt werden können.|
|**Codeanalyse für verwalteten Code erzwingen**|Erfordert, dass alle verwalteten Projekte odeanalyse ausführen und zu erstellen, bevor sie eingecheckt werden können.|

## <a name="to-specify-a-managed-rule-set"></a>Um einen verwalteten Regelsatz anzugeben.

Von der **diesen Regelsatz ausführen** aufzulisten, verwenden Sie eine der folgenden Methoden:

- Wählen Sie einen Microsoft-standard-Regelsatz.

- Wählen Sie eine benutzerdefinierte Regel festlegen, indem Sie auf  **\<Regelsatz auswählen aus der Quellcodeverwaltung... >**. Geben Sie dann den Versionskontrollpfad des Regelsatzes im Browser-Steuerelement Quelle. Die Syntax der einen Pfad für die Versionskontrolle ist:

   **$/** `TeamProjectName` **/** `VersionControlPath`

Weitere Informationen zum Erstellen und Implementieren einer benutzerdefinierte Eincheckrichtlinie Regel festlegen, finden Sie unter [Implementieren von benutzerdefinierten Eincheckrichtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).

## <a name="see-also"></a>Siehe auch

- [Erstellen und Verwenden von Eincheckrichtlinien für die Analyse](../code-quality/how-to-create-or-update-standard-code-analysis-check-in-policies.md)