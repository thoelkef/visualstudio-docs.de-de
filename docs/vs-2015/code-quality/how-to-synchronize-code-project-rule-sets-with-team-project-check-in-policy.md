---
title: 'Vorgehensweise: Synchronisieren von Code Projekt-Regelsätzen mit der Eincheck Richtlinie für Team Projekte | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3c6e7550940f9d2efa5ca228123310f1b861ee76
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651598"
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Gewusst wie: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Code Analyse Einstellungen für Code Projekte werden mit der Eincheck Richtlinie für das Teamprojekt synchronisiert, indem ein Regelsatz angegeben wird, der mindestens die Regeln enthält, die im Regelsatz für die Eincheck Richtlinie angegeben sind. Ihr Entwickler Leiter kann Sie über den Namen und den Speicherort des Regelsatzes für die Eincheck Richtlinie informieren. Sie können eine der folgenden Optionen verwenden, um sicherzustellen, dass die Code Analyse für das Projekt den richtigen Regelsatz verwendet:

- Wenn die Eincheck Richtlinie einen der integrierten Microsoft-Regelsätze verwendet, öffnen Sie das Dialogfeld "Eigenschaften" für das Code Projekt, zeigen Sie die Seite "Code Analyse" an, und wählen Sie den Regelsatz auf der Seite "Code Analyse" der Code Projekteinstellungen aus. Die Standardregel Sätze von Microsoft werden automatisch mit Visual Studio installiert und sollten nicht bearbeitet werden. Wenn die Regelsätze nicht bearbeitet werden, entsprechen die Regeln in der Richtlinie und den lokalen Regelsätzen der Garantie.

- Wenn in der Eincheck Richtlinie ein benutzerdefinierter Regelsatz verwendet wird, führen Sie einen Get-Vorgang für die Regel Satz Datei in der Versionskontrolle aus, um eine lokale Kopie zu erstellen. Geben Sie dann den lokalen Speicherort in den Code Analyse Einstellungen für das Code Projekt an. Die Regeln entsprechen garantiert, wenn der Regelsatz für die Eincheck Richtlinie auf dem neuesten Stand ist.

     Wenn Sie den Speicherort der Versionskontrolle einem lokalen Ordner zuordnen, der sich in derselben Beziehung zum Teamprojekt Stamm wie das Code Projekt befindet, wird der Speicherort der Regel mit einem relativen Pfad festgelegt. Der relative Pfad stellt sicher, dass die Code Projekteinstellung für die Code Analyse auf andere Computer verschoben werden kann.

- Passen Sie eine Kopie des Regelsatzes für die Eincheck Richtlinie für ein Code Projekt an. Stellen Sie sicher, dass der neue Regelsatz alle Regeln in der Eincheck Richtlinie und alle anderen Regeln enthält, die Sie einschließen möchten. Sie müssen sicherstellen, dass der Regelsatz alle Regeln im Regelsatz für die Eincheck Richtlinie enthält.

### <a name="to-specify-a-microsoft-standard-rule-set"></a>So geben Sie einen Microsoft Standard-Regelsatz an

1. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Code Projekt, und klicken Sie dann auf **Eigenschaften**.

2. Klicken Sie auf **Code Analyse**.

3. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf den Regelsatz Check-in-Richtlinie.

### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>So geben Sie einen benutzerdefinierten Eincheck Richtlinien-Regelsatz an

1. Führen Sie bei Bedarf einen Get-Vorgang für die Regel Satz Datei aus, die die Eincheck Richtlinie angibt.

2. Klicken Sie in **Projektmappen-Explorer**mit der rechten Maustaste auf das Code Projekt, und klicken Sie dann auf **Eigenschaften**.

3. Klicken Sie auf **Code Analyse**.

4. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Browse... >** .

5. Geben Sie im Dialogfeld **Öffnen** die Regel Satz Datei für die Eincheck Richtlinie an.

### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>So erstellen Sie einen benutzerdefinierten Regelsatz für ein Code Projekt

1. Führen Sie eines der Verfahren weiter oben in diesem Thema aus, um die Eincheck Richtlinie für das Teamprojekt auf der Seite "Code Analyse" des Dialog Felds "Projekteinstellungen" auszuwählen.

2. Klicken Sie auf **Öffnen**.

3. Hinzufügen oder Entfernen von Regeln mithilfe des Regelsatz-Editors.

     Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).

4. Speichern Sie den geänderten Regelsatz in einer RuleSet-Datei auf dem lokalen Computer oder in einem UNC-Pfad.

5. Öffnen Sie das Dialogfeld "Eigenschaften" für das Code Projekt, und zeigen Sie die Seite " **Code Analyse** " an.

6. Klicken Sie in der Liste **diesen Regelsatz ausführen** auf **\<Browse... >** .

7. Geben Sie im Dialogfeld **Öffnen** die Regel Satz Datei an.
