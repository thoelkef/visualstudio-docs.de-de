---
title: 'Vorgehensweise: Unterdrücken von Warnungen über das Menüelement | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 1c756a5ab6516d78f5370622555898c98658e8b3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49211783"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Gewusst wie: Unterdrücken von Warnungen über das Menüelement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
>  In der Quelle wird die Unterdrückung für Websiteprojekte nicht unterstützt.  
  
 Das Fenster "Codeanalyse" können Warnungen der Codeanalyse unterdrückt werden sollen. Unterdrücken eine Warnung ist nicht identisch mit deaktivieren. Wenn Sie eine Warnung unterdrücken, gilt sie nur für eine bestimmte Instanz des Verstoßes. Andere Verstöße gegen die gleichen Warnung werden weiterhin in das Fenster "Fehlerliste" gemeldet.  
  
 Nachdem Sie die Codeanalyse ausführen, kann bestimmt werden, dass mindestens eine der Warnungen der Codeanalyse im codeanalysefenster angezeigt werden, die nicht für Ihre Anwendung gelten. Beispielsweise können Sie bestimmen, dass der Code korrekt unverändert ist. Oder möglicherweise der Fall, dass einige Verstöße mit niedriger Priorität und nicht in den aktuellen Entwicklungszyklus behoben werden werden. Ungeachtet der Ursache ist es häufig nützlich, um anzugeben, dass die Warnung nicht zutreffend, können Mitgliedern Ihres Teams, die wissen, dass der Code überprüft wurde und festgestellt wurde, dass die Warnung unterdrückt werden kann. Im Quellcode ist Unterdrückung nützlich, da können Sie die put einer Unterdrückung in der Nähe, in dem die Warnung generiert wird.  
  
 Sie können auswählen, ob die Unterdrückung im Quellcode oder in der globale Unterdrückungsdatei angezeigt wird. Einige Unterdrückungen müssen in der globale Unterdrückungsdatei platziert werden. Wenn dies der Fall ist die **In Quelle** die Option deaktiviert.  
  
### <a name="to-suppress-a-warning-by-using-menu-item"></a>Eine Warnung zu unterdrücken, über Menüelement  
  
1.  Auf der **analysieren** Menü wählen **Windows** und wählen Sie dann **Codeanalyse**.  
  
2.  In der **Codeanalyse** Fenster, wählen Sie die Warnung unterdrücken.  
  
3.  Wählen Sie die Aktionen, und wählen Sie dann **Nachrichten unterdrücken**, und wählen Sie dann entweder **In Quelle** oder **In Projektunterdrückungsdatei**.  
  
     Die betreffende Warnung unterdrückt wird, und die Warnung wird im Fenster "Codeanalyse" durchgestrichen angezeigt.  
  
> [!NOTE]
>  Unterdrückungen, die kein Ziel verfügen, die in der Datei globale Unterdrückung angezeigt werden.



