---
title: "Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien f&#252;r die Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.policyeditor"
helpviewer_keywords: 
  - "Codeanalyse, Migrieren der Eincheckrichtlinie"
ms.assetid: 458eb3b8-bb5e-4056-82b7-7079ce9c4089
caps.latest.revision: 29
caps.handback.revision: 29
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Erstellen oder Aktualisieren von Standardeincheckrichtlinien f&#252;r die Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können mithilfe der Eincheckrichtlinie für die Codeanalyse festlegen, dass die Codeanalyse für alle Codeprojekte eines Teamprojekts ausgeführt werden muss.  Wenn die Codeanalyse als erforderlich festgelegt wird, kann dies die Qualität des in die CodeBase eingecheckten Codes verbessern.  
  
> [!NOTE]
>  Dieses Feature ist nur bei Verwendung von Team Foundation Server verfügbar.  
  
 Eincheckrichtlinien für die Codeanalyse werden in den Teamprojekteinstellungen festgelegt, und sie gelten für jedes Codeprojekt im Teamprojekt.  Die Ausführung der Codeanalyse wird für Codeprojekte in der Projektdatei \(.xxproj\) des Codeprojekts konfiguriert.  Die Codeanalyse wird auf dem lokalen Computer ausgeführt.  Wenn Sie eine Eincheckrichtlinie für die Codeanalyse aktivieren, müssen einzucheckende Dateien in einem Codeprojekt nach der letzten Bearbeitung kompiliert werden, und eine Codeanalyse, die mindestens die Regeln in den Teamprojekteinstellungen enthält, muss auf dem Computer ausgeführt werden, auf dem die Änderungen vorgenommen wurden.  
  
-   Für verwalteten Code legen Sie die Eincheckrichtlinie durch die Angabe eines *Regelsatzes* fest, der eine Teilmenge der Codeanalyseregeln enthält.  
  
-   Für C\/C\+\+\-Code erfordert die Eincheckrichtlinie, dass alle Codeanalyseregeln ausgeführt werden.  Sie können Präprozessordirektiven hinzufügen, um bestimmte Regeln für die einzelnen Codeprojekte im Teamprojekt zu deaktivieren.  
  
 Nachdem Sie eine Eincheckrichtlinie für verwalteten Code angegeben haben, können Teammitglieder die Codeanalyseeinstellungen für Codeprojekte mit den Teamprojekt\-Richtlinieneinstellungen synchronisieren.  
  
### So öffnen Sie den Eincheckrichtlinien\-Editor  
  
1.  Klicken Sie in Team Explorer mit der rechten Maustaste auf den Namen des Teamprojekts, zeigen Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
2.  Wählen Sie im Dialogfeld **Quellcodeverwaltung** die Registerkarte **Eincheckrichtlinien** aus.  
  
3.  Führen Sie eine der folgenden Aktionen aus:  
  
    -   Klicken Sie auf **Hinzufügen**, um eine neue Eincheckrichtlinie zu erstellen.  
  
    -   Doppelklicken Sie in der Liste **Richtlinientyp** auf das vorhandene Element **Codeanalyse**, um die Richtlinie zu ändern.  
  
### So legen Sie Richtlinienoptionen fest  
  
-   Aktivieren oder deaktivieren Sie die folgenden Optionen:  
  
    |Option|**Beschreibung**|  
    |------------|----------------------|  
    |**Einchecken von Dateien erzwingen, sodass nur Dateien enthalten sind, die Teil der aktuellen Lösung sind**|Die Codeanalyse kann nur für Dateien ausgeführt werden, die in Projektmappen\- und Projektkonfigurationsdateien angegeben sind.  Diese Richtlinie stellt sicher, dass sämtlicher Code, der Teil einer Projektmappe ist, analysiert wird.|  
    |**C\/C\+\+\-Codeanalyse erzwingen \(\/analyze\)**|Erfordert, dass alle C\- oder C\+\+\-Projekte mit der \/analyze\-Compileroption erstellt werden, damit die Codeanalyse ausgeführt wird, bevor sie eingecheckt werden können.|  
    |**Codeanalyse für verwalteten Code erzwingen**|Erfordert, dass für alle verwalteten Projekte Codeanalyse und Builderstellung ausgeführt werden, bevor sie eingecheckt werden können.|  
  
### So geben Sie einen Regelsatz für verwalteten Code an  
  
-   Verwenden Sie in der Dropdownliste **Diesen Regelsatz ausführen** eine der folgenden Methoden:  
  
    -   Wählen Sie einen Microsoft\-Standardregelsatz aus.  
  
    -   Um einen benutzerdefinierten Regelsatz auszuwählen, klicken Sie auf **\<Ausgewählter Regelsatz aus der Quellcodeverwaltung...\>** und geben Sie den Versionskontrollpfad des Regelsatzes im Browser der Quellcodeverwaltung ein.  Syntax für einen Versionskontrollpfad:  
  
    -   **$\/** `TeamProjectName` **\/** `VersionControlPath`  
  
    -   Weitere Informationen zum Erstellen und Implementieren eines benutzerdefinierten Eincheckrichtlinien\-Regelsatzes finden Sie unter [Implementieren von benutzerdefinierten Eincheckrichtlinien für verwalteten Code](../code-quality/implementing-custom-code-analysis-check-in-policies-for-managed-code.md).  
  
## Siehe auch  
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)