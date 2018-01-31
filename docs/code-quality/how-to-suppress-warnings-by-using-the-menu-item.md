---
title: "Vorgehensweise: Unterdrücken von Warnungen über das Menüelement | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 5ce2369b5b97f1767a17686d3de2d4127150c05d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Gewusst wie: Unterdrücken von Warnungen über das Menüelement
> [!NOTE]
>  In der Quelle ist die Unterdrückung für Websiteprojekte nicht unterstützt.  
  
 Codeanalysefenster können zum Unterdrücken der codeanalysewarnungen. Unterdrücken eine Warnung ist nicht identisch mit der Deaktivierung. Wenn Sie eine Warnung zu unterdrücken, gilt er nur für eine bestimmte Instanz des Verstoßes. Weiteren Verletzungen der gleichen Warnung werden weiterhin in das Fenster "Fehlerliste" angezeigt.  
  
 Nachdem Sie die Codeanalyse ausführen, können Sie ermitteln, dass eine oder mehrere der Warnungen der Codeanalyse im codeanalysefenster angezeigt werden nicht für Ihre Anwendung gelten. Beispielsweise können Sie ermitteln, dass der Code korrekt ist. Alternativ ist es möglicherweise der Fall, dass einige Verstöße mit niedriger Priorität und werden nicht in der aktuellen Entwicklungszyklus behoben. Unabhängig von der Ursache ist es häufig nützlich, um anzugeben, dass die Warnung ist nicht anwendbar, lassen die Teammitglieder, die wissen, dass der Code überprüft wurde und festgestellt wurde, dass die Warnung unterdrückt werden konnte. Im Quellcode ist Unterdrückung nützlich, da es ermöglicht eine Unterdrückung in der Nähe, wo die Warnung generiert wird.  
  
 Sie können auswählen, ob die Unterdrückung im Quellcode oder in der globalen Unterdrückungsdatei angezeigt wird. Einige Unterdrückungen müssen in der globalen Unterdrückungsdatei eingefügt werden. Wenn dies der Fall ist die **In Quelle** die Option deaktiviert.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Zum Unterdrücken einer Warnung mithilfe von Menüelement  
  
1.  Auf der **analysieren** Menü wählen **Windows** und wählen Sie dann **Codeanalyse**.  
  
2.  In der **Codeanalyse** Fenster, wählen Sie die Warnung unterdrücken.  
  
3.  Wählen Sie die Aktionen, und wählen Sie dann **Meldung(en) unterdrücken**, und wählen Sie dann entweder **In Quelle** oder **im Projektunterdrückungsdatei**.  
  
     Die betreffende Warnung wird unterdrückt, und die Warnung wird im Fenster "Codeanalyse" durchgestrichen angezeigt.  
  
> [!NOTE]
>  Unterdrückungen, die nicht über ein Ziel verfügen werden in der globalen Unterdrückungsdatei angezeigt.