---
title: "Gewusst wie: Festlegen von Codeanalyseeigenschaften f&#252;r C/C++-Projekte | Microsoft Docs"
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
  - "vs.codeanalysis.propertypages.native"
  - "VC.Project.VCCLCompilerTool.EnablePrefast"
  - "VC.Project.VCFxCopTool.EnablePREfast"
  - "VC.Project.VCFxCopTool.IgnoreGeneratedCode"
helpviewer_keywords: 
  - "C/C++-Codeanalyseeigenschaften"
  - "Codeanalyseeigenschaften"
  - "Eigenschaften, C/C++-Codeanalyse"
  - "Eigenschaften, Codeanalyse"
ms.assetid: 7af52097-6d44-4785-9b9f-43b7a7d447d7
caps.latest.revision: 17
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Gewusst wie: Festlegen von Codeanalyseeigenschaften f&#252;r C/C++-Projekte
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können konfigurieren, welche Regeln vom Codeanalysetool verwendet werden, um Code in den einzelnen Projektkonfigurationen zu analysieren.  Darüber hinaus können Sie die Codeanalyse anweisen, Warnungen aus dem Code zu unterdrücken, die durch ein Tool eines Drittanbieters generiert und dem Projekt hinzugefügt wurden.  
  
## Eigenschaftenseite Codeanalyse  
 Die Eigenschaftenseite **Codeanalyse** enthält alle Codeanalyse\-Konfigurationseinstellungen für ein Projekt.  Um die Eigenschaftenseite für die Codeanalyse für ein Projekt im **Projektmappen\-Explorer** zu öffnen, klicken Sie mit der rechten Maustaste auf das Projekt und klicken dann auf **Eigenschaften**.  Erweitern Sie dann **Konfigurationseigenschaften**, und wählen Sie die Registerkarte **Codeanalyse** aus.  
  
## Projektkonfiguration und Plattform  
 Über die Listen **Konfiguration** und **Plattform** können Sie unterschiedliche Codeanalyseeinstellungen auf verschiedene Projektkonfigurations\- und Plattformkombinationen anwenden.  Beispielsweise können Sie die Codeanalyse anweisen, für Debugbuilds eine andere Regelgruppe als für Releasebuilds auf das Projekt anzuwenden.  
  
## Aktivieren der Codeanalyse  
 Sie können entscheiden, ob die Codeanalyse für das Projekt aktiviert werden soll, indem Sie die Option **Codeanalyse für C\/C\+\+ für Build aktivieren** auswählen.  In Kombination mit der Liste **Konfiguration** könnten Sie sich z. B. entscheiden, die Codeanalyse für Debugbuilds zu deaktivieren und für Releasebuilds zu aktivieren.  
  
 Wenn das Projekt verwalteten Code enthält, können Sie entscheiden, ob die Codeanalyse aktiviert oder deaktiviert werden soll, indem Sie die Option **Codeanalyse für Build aktivieren** auswählen.  
  
 Die Codeanalyse soll Ihnen helfen, die Codequalität zu verbessern und allgemeine Fehler zu vermeiden.  Deshalb sollten Sie sorgfältig abwägen, bevor Sie die Codeanalyse deaktivieren.  Es empfiehlt sich normalerweise, Regelsätze oder einzelne Regeln zu deaktivieren, die nicht auf das Projekt angewendet werden sollen.  
  
## Generierter Code  
 Entwickler verwenden oft Tools, um die Anwendungsentwicklung zu beschleunigen.  Diese Tools können Code generieren, der dem Projekt hinzugefügt wird.  Möglicherweise möchten Sie die Regelverletzungen anzeigen, die die Codeanalyse in generiertem Code ermittelt.  Allerdings sollten diese Verletzungen vielleicht nicht angezeigt werden, wenn der Code nicht verwaltet werden soll.  
  
 Mit dem Kontrollkästchen **Ergebnisse aus generiertem Code unterdrücken** auf der Eigenschaftenseite **Allgemein** können Sie festlegen, ob Codeanalysewarnungen aus verwaltetem Code angezeigt werden, der durch ein Drittanbietertool generiert wurde.  
  
## Regelsätze  
 Wenn das Projekt verwalteten Code enthält, können Sie die Regeln auswählen, die in einer Codeanalyse angewendet werden sollen, indem Sie einen Regelsatz aus der Liste **Diesen Regelsatz ausführen** auswählen.  
  
## Siehe auch  
 [Analysieren der Qualität von verwaltetem Code](../code-quality/analyzing-managed-code-quality-by-using-code-analysis.md)   
 [Codeanalyse für C\/C\+\+\-Warnungen](../code-quality/code-analysis-for-c-cpp-warnings.md)