---
title: "Problembehandlung für Codemetrikfehler | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: "4"
author: erickson-doug
ms.author: douge
manager: douge
ms.openlocfilehash: 6dde34ce4808f21a90fa9d2e37daf7ed88d4e7fa
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="troubleshooting-code-metrics-issues"></a>Problembehandlung für Codemetrikfehler
Beim Sammeln von Codemetriken stoßen Sie möglicherweise auf folgende Probleme:  
  
-   [Änderung in der Berechnung von Codekomplexität in Visual Studio 2010](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Änderung in der Berechnung von Codekomplexität in Visual Studio 2010  
 Die Codekomplexitätsmetrik, die in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] berechnet wurde, kann sich in folgenden Szenarios für die gleiche Funktion von der Metrik unterscheiden, die von früheren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] berechnet wurde:  
  
-   Die Funktion enthält mindestens einen Catch-Block. In früheren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] waren Catch-Blöcke nicht in der Berechnung enthalten. Bei [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] wird die Komplexität jedes einzelnen Catch-Blocks zu der Komplexität der Funktion hinzugefügt.  
  
-   Die Funktion enthält eine switch-Anweisung (Select Case in Visual Basic). Unterschiede der Compiler zwischen [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und früheren Versionen können bei manchen switch-Anweisungen, die Fall-Through-Fälle beinhalten, unterschiedlichen MSIL-Code generieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)