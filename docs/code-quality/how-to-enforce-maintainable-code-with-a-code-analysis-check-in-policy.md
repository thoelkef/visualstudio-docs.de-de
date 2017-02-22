---
title: "Gewusst wie: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie f&#252;r die Codeanalyse | Microsoft Docs"
ms.custom: ""
ms.date: "12/12/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Codeanalyse, Eincheckrichtlinien"
ms.assetid: d1b3b04f-4dd9-40e6-b2d4-b414d33fb647
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Gewusst wie: Erzwingen von wartbarem Code mit einer Eincheckrichtlinie f&#252;r die Codeanalyse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Entwickler können mit dem Codemetriktool die Komplexität und Verwaltbarkeit ihres Codes messen, sie können Codemetrik jedoch nicht als Teil einer Eincheckrichtlinie aufrufen.  Ein Team kann jedoch Codeanalyseregeln aktivieren, die die Einhaltung von Codemetrikstandards überprüfen und und die Regeln über Eincheckrichtlinien durchsetzen.  Weitere Informationen zur Codemetrik finden Sie unter [Codemetrikwerte](../code-quality/code-metrics-values.md).  
  
 Entwickler können die Regeln zu Vererbungstiefe, Klassenkopplung, Wartbarkeitsindex und Komplexität aktivieren, um verwaltbaren Code durch Eincheckrichtlinien für die Codeanalyse zu erzwingen.  Alle vier Regeln befinden sich unter der Kategorie "Wartbarkeitsregeln" im Codeanalyserichtlinien\-Editor.  
  
 Administratoren der [!INCLUDE[esprfound](../code-quality/includes/esprfound_md.md)]\-Versionskontrolle können die Wartbarkeitsregeln der Codeanalyse zu den Anforderungen für die Eincheckrichtlinie hinzufügen.  Für diese Eincheckrichtlinien müssen Entwickler die Codeanalyse anhand dieser Regeländerungen ausführen, bevor sie einen Eincheckvorgang initiieren.  
  
### So öffnen Sie den Codeanalyserichtlinien\-Editor  
  
1.  Klicken Sie in **Team Explorer** mit der rechten Maustaste auf das Teamprojekt, klicken Sie auf **Teamprojekteinstellungen**, und klicken Sie dann auf **Quellcodeverwaltung**.  
  
     Das Dialogfeld **Quellcodeverwaltung** wird angezeigt.  
  
2.  Klicken Sie auf die Registerkarte **Eincheckrichtlinien** und dann auf **Hinzufügen**.  
  
     Das Dialogfeld **Eincheckrichtlinie hinzufügen** wird angezeigt.  
  
3.  Aktivieren Sie in der Liste **Eincheckrichtlinien** das Kontrollkästchen **Codeanalyse**, und klicken Sie dann auf **OK**.  
  
     Das Dialogfeld **Codeanalyserichtlinien\-Editor** wird angezeigt.  
  
### So aktivieren Sie Wartbarkeitsregeln für die Codeanalyse  
  
1.  Erweitern Sie im Dialogfeld **Codeanalyserichtlinien\-Editor** unter **Regeleinstellungen** den Knoten **Wartbarkeitsregeln**.  
  
2.  Aktivieren Sie die Kontrollkästchen für die folgenden Regeln:  
  
    -   Vererbungstiefe: **CA1501 AvoidExcessiveInheritance** \- Schwellenwert: Warnung bei einer Tiefe von mehr als fünf Ebenen  
  
    -   Komplexität: **CA1502 AvoidExcessiveComplexity** \- Schwellenwert: Warnung bei mehr als 25  
  
    -   Wartbarkeitsindex: **CA1505 AvoidUnmaintainableCode** \- Schwellenwert: Warnung bei Unterschreiten von 20  
  
    -   Klassenkopplung: **CA1506 AvoidExcessiveClassCoupling** \- Schwellenwert: Warnung bei Überschreiten von 80 für eine Klasse und 30 für eine Methode  
  
    -   Wenn Sie darüber hinaus festlegen möchten, dass ein Regelverstoß einen Build verhindert, aktivieren Sie das Kontrollkästchen **Warnung als Fehler behandeln** neben der Regelbeschreibung.  
  
3.  Klicken Sie auf **OK**.  Die neuen Eincheckrichtlinien gelten ab sofort bei Eincheckvorgängen.  
  
## Siehe auch  
 [Codemetrikwerte](../code-quality/code-metrics-values.md)   
 [Erstellen und Verwenden von Eincheckrichtlinien für die Codeanalyse](../code-quality/creating-and-using-code-analysis-check-in-policies.md)