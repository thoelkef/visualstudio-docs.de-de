---
title: "Gewusst wie: Synchronisieren der Regels&#228;tze f&#252;r Codeprojekte mit der Team Project-Eincheckrichtlinie | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.selecttfsruleset"
ms.assetid: 9b02f934-2db6-41ec-aaff-9c31ceec2f04
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Synchronisieren der Regels&#228;tze f&#252;r Codeprojekte mit der Team Project-Eincheckrichtlinie
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie synchronisieren die Codeanalyseeinstellungen für Codeprojekte mit der Eincheckrichtlinie für das Teamprojekt, indem Sie einen Regelsatz angeben, der mindestens die Regeln enthält, die im Regelsatz für die Eincheckrichtlinie angegeben werden.  Der leitende Entwickler kann Ihnen den Namen und den Speicherort des Regelsatzes für die Eincheckrichtlinie mitteilen.  Mit den folgenden Optionen können Sie sicherstellen, dass die Codeanalyse für das Projekt den richtigen Regelsatz verwendet:  
  
-   Wenn von der Eincheckrichtlinie einer der integrierten Regelsätze von Microsoft verwendet wird, öffnen Sie das Eigenschaftendialogfeld für das Codeprojekt, zeigen Sie die Seite "Codeanalyse" an, und wählen Sie den Regelsatz auf der Seite "Codeanalyse" der Codeprojekteinstellungen aus.  Die Microsoft\-Standardregelsätze werden automatisch mit Visual Studio werden festgelegt auf schreibgeschützt und dürfen nicht bearbeitet werden.  Wenn die Regelsätze nicht bearbeitet werden, stimmen die Regeln in der Richtlinie und die lokalen Regelsätze garantiert überein.  
  
-   Wenn die Eincheckrichtlinie einen benutzerdefinierten Regelsatz verwendet, führen Sie einen GET\-Vorgang für die Regelsatzdatei in der Versionskontrolle aus, um eine lokale Kopie zu erstellen.  Geben Sie dann diesen lokalen Speicherort in den Codeanalyseeinstellungen für das Codeprojekt an.  Die Regeln passen dann garantiert zusammen, wenn der Regelsatz für die Eincheckrichtlinie auf dem neuesten Stand ist.  
  
     Wenn Sie den Speicherort der Versionskontrolle einem lokalen Ordner zuordnen, der in der gleichen Beziehung zum Teamprojektstamm wie das Codeprojekt steht, wird der Speicherort der Regel mithilfe eines relativen Pfads festgelegt.  Durch den relativen Pfad wird gewährleistet, dass die Codeprojekteinstellung für die Codeanalyse auf andere Computer verschoben werden kann.  
  
-   Passen Sie eine Kopie des Regelsatzes für die Eincheckrichtlinie für ein Codeprojekt an.  Stellen Sie sicher, dass der neue Regelsatz alle Regeln in der Eincheckrichtlinie und beliebige andere Regeln enthält, dass Sie einschließen möchten.  Sie müssen sicherstellen, dass der Regelsatz alle Regeln im Regelsatz für die Eincheckrichtlinie einschließt.  
  
### So geben Sie einem Microsoft\-Standardregelsatz an  
  
1.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
2.  Klicken Sie auf **Codeanalyse**.  
  
3.  Klicken Sie in der Liste **Diesen Regelsatz ausführen** auf den Eincheckrichtlinien\-Regelsatz.  
  
### So geben Sie einen benutzerdefinierten Eincheckrichtlinien\-Regelsatz an  
  
1.  Führen Sie ggf. einen GET\-Vorgang für die Regelsatzdatei aus, die die Eincheckrichtlinie angibt.  
  
2.  Klicken Sie im Projektmappen\-Explorer mit der rechten Maustaste auf das Codeprojekt, und klicken Sie dann auf **Eigenschaften**.  
  
3.  Klicken Sie auf **Codeanalyse**.  
  
4.  In der Liste **Diesen Regelsatz ausführen** klicken Sie auf **\<Durchsuchen...\>**.  
  
5.  Geben Sie im Dialogfeld **Öffnen** die Eincheckrichtlinien\-Regelsatzdatei an.  
  
### So erstellen Sie einen benutzerdefinierten Regelsatz für ein Codeprojekt  
  
1.  Führen Sie eines der weiter oben in diesem Thema genannten Verfahren aus, um die Eincheckrichtlinie des Teamprojekts auf der Codeanalyseseite im Dialogfeld mit den Projekteinstellungen auszuwählen.  
  
2.  Klicken Sie auf **Öffnen**.  
  
3.  Verwenden Sie den Regelsatz\-Editor zum Hinzufügen oder Entfernen von Regeln.  
  
     Weitere Informationen finden Sie unter [Erstellen von benutzerdefinierten Regelsätzen](../code-quality/creating-custom-code-analysis-rule-sets.md).  
  
4.  Speichern Sie den geänderten Regelsatz in einer .ruleset\-Datei auf dem lokalen Computer oder in einem UNC\-Pfad.  
  
5.  Öffnen Sie das Eigenschaftendialogfeld für das Codeprojekt, und zeigen Sie die Seite **Codeanalyse** an.  
  
6.  In der Liste **Diesen Regelsatz ausführen** klicken Sie auf **\<Durchsuchen...\>**.  
  
7.  Geben Sie im Dialogfeld **Öffnen** die Regelsatzdatei an.