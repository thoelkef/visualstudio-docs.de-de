---
title: "Problembehandlung für Codemetrikfehler | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: ea1e787c1d509123a650cf2bd20e5fa8bffd5b4e
ms.openlocfilehash: 9f3f41548412d84cd1219aae45b7c87ea5383de9
ms.contentlocale: de-de
ms.lasthandoff: 09/26/2017

---
# <a name="troubleshooting-code-metrics-issues"></a>Problembehandlung für Codemetrikfehler
Sie können beim Sammeln von Codemetrik einige der folgenden Probleme auftreten:  
  
-   [Änderungen in Visual Studio 2010 Code Komplexität Berechnungen](#Changes_in_Visual_Studio_2010_code_complexity_calculations)  
  
##  <a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a>Änderungen in Visual Studio 2010 Code Komplexität Berechnungen  
 Für die gleiche Funktion berechnet den Code Komplexität Metrik [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] kann von der Berechnung von früheren Versionen von anderen [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] für den folgenden Situationen:  
  
-   Die Funktion enthält ein oder mehrere catch-Blöcke. In früheren Versionen von [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], Catch-Blöcke nicht in die Berechnung eingeschlossen. In [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)], die Komplexität der einzelnen Catch-Block um die Komplexität der Funktion hinzugefügt wird.  
  
-   Die Funktion enthält eine Switch (Select Case in VB)-Anweisung. Compilerfehler Unterschiede zwischen [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und frühere Versionen können unterschiedlichen MSIL-Code für einige Switch-Anweisungen, die fallen über Fälle enthalten generieren.  
  
## <a name="see-also"></a>Siehe auch  
 [Messen von Komplexität und Verwaltbarkeit verwalteten Codes](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
