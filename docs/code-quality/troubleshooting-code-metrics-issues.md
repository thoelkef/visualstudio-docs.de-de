---
title: "Problembehandlung f&#252;r Codemetrikfehler | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: "erickson-doug"
ms.author: "douge"
manager: "douge"
caps.handback.revision: 4
---
# Problembehandlung f&#252;r Codemetrikfehler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Beim Sammeln von Codemetrikdaten treten unter Umständen einige der folgenden Probleme auf:  
  
-   [Änderungen in den Visual Studio 2010\-Berechnungen für die Codekomplexität](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Änderungen in den Visual Studio 2010\-Berechnungen für die Codekomplexität  
 In den folgenden Situationen kann sich die in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] berechnete Codekomplexitätsmetrik einer Funktion von der Berechnung in älteren [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]\-Versionen unterscheiden:  
  
-   Die Funktion enthält mindestens einen Catch\-Block.  In älteren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] wurden Catch\-Blöcke bei der Berechnung nicht berücksichtigt.  In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] wird die Komplexität jedes Catch\-Blocks der Komplexität der Funktion hinzugefügt.  
  
-   Die Funktion enthält eine Switch\-Anweisung \("Select Case" in VB\).  Aufgrund von Compilerunterschieden zwischen [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und älteren Versionen wird für einige Switch\-Anweisungen mit FallThrough unter Umständen unterschiedlicher MSIL\-Code generiert.  
  
## Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)