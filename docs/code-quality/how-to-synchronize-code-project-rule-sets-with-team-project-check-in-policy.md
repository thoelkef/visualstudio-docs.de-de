---
title: "Vorgehensweise: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.codeanalysis.selecttfsruleset
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: de3a7bfaccec45dc6b7fce1def45a6e6de8e75f2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-synchronize-code-project-rule-sets-with-team-project-check-in-policy"></a>Gewusst wie: Synchronisieren der Regelsätze für Codeprojekte mit der Team Project-Eincheckrichtlinie
Synchronisieren Sie die codeanalyseeinstellungen für Codeprojekte, die in der Eincheckrichtlinie für das Teamprojekt durch Angabe eines Regelsatzes, das mindestens die Regeln enthält, die in der Regel legen Sie für die Eincheckrichtlinie angegeben werden. Der leitende Entwickler können Sie den Namen und den Speicherort des Regelsatzes für die Eincheckrichtlinie informieren. Sie können eine der folgenden Optionen verwenden, um sicherzustellen, dass die Codeanalyse für das Projekt den richtigen Satz von Regeln verwendet:  
  
-   Wenn der Eincheckrichtlinie eines integrierten Microsoft-Regelsätze verwendet wird, öffnen Sie das Eigenschaftendialogfeld für das Codeprojekt, dort die Seite "Codeanalyse" und wählen Sie die Regel, die auf der Seite "Codeanalyse" von den projekteinstellungen Code festlegen. Die Microsoft-Standardregelsätze automatisch mit Visual Studio installiert werden auf schreibgeschützt festgelegt werden und sollte nicht bearbeitet werden. Wenn die Regelsätze nicht bearbeitet werden, die Regeln in der Richtlinie und die lokalen Regelsätze garantiert überein.  
  
-   Wenn die in der Eincheckrichtlinie für einen benutzerdefinierten Regelsatz verwendet wird, führen Sie einen Get-Vorgang für die Regelsatzdatei in der Versionskontrolle, um eine lokale Kopie zu erstellen. Geben Sie dann diesen lokalen Speicherort in den Code Analysis-Einstellungen für das Codeprojekt an. Die Regeln sind garantiert entsprechen, wenn der Regelsatz für die Eincheckrichtlinie auf dem neuesten Stand ist.  
  
     Wenn Sie den Speicherort der Versionskontrolle in einen lokalen Ordner, die in der gleichen Beziehung zum Teamprojektstamm als das Codeprojekt ist zuordnen, wird der Speicherort der Regel über einen relativen Pfad festgelegt. Der relative Pfad wird sichergestellt, dass der Code projekteinstellung für die Codeanalyse auf andere Computer verschoben werden kann.  
  
-   Passen Sie eine Kopie des Regelsatzes für die Eincheckrichtlinie für ein Codeprojekt an. Stellen Sie sicher, dass die neuen Regelsatz enthält alle Regeln in der Eincheckrichtlinie und beliebige andere Regeln, die Sie einschließen möchten. Sie müssen sicherstellen, dass Ihre Regelsatz alle Regeln im Regelsatz für die Eincheckrichtlinie enthält.  
  
### <a name="to-specify-a-microsoft-standard-rule-set"></a>Geben Sie eine Microsoft-standard-Regel fest  
  
1.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Codeanalyse**.  
  
3.  In der **diesen Regelsatz ausführen** Liste, wählen Sie den Regelsatz in der Eincheckrichtlinie.  
  
### <a name="to-specify-a-custom-check-in-policy-rule-set"></a>Angeben einen benutzerdefinierten Eincheckrichtlinie-Regelsatz  
  
1.  Führen Sie bei Bedarf einen Get-Vorgang für die Regelsatzdatei an, die angibt, die in der Eincheckrichtlinie.  
  
2.  In **Projektmappen-Explorer**mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf **Codeanalyse**.  
  
4.  In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.  
  
5.  In der **öffnen** Dialogfeld Feld, in der Eincheckrichtlinie für die Regelsatz Datei anzugeben.  
  
### <a name="to-create-a-custom-rule-set-for-a-code-project"></a>Legen Sie zum Erstellen eines benutzerdefinierten Regelsatzes für ein Codeprojekt  
  
1.  Führen Sie eines der Verfahren in diesem Thema die Eincheckrichtlinie für das Teamprojekt auf der Seite "Codeanalyse" im Dialogfeld Projekt Einstellungen auswählen.  
  
2.  Klicken Sie auf **öffnen**.  
  
3.  Hinzufügen oder Entfernen von Regeln mithilfe der Regelsatz-Editor.  
  
     Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Speichern der geänderten Regelsatzes in einer RULESET-Datei auf dem lokalen Computer oder einem UNC-Pfad an.  
  
5.  Öffnen Sie das Eigenschaftendialogfeld für das Codeprojekt, und zeigen die **Codeanalyse** Seite.  
  
6.  In der **diesen Regelsatz ausführen** auf  **\<durchsuchen... >**.  
  
7.  In der **öffnen** Dialogfeld geben die Regelsatz-Datei.