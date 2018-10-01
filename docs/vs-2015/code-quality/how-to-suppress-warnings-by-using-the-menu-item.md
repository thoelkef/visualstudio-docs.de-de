---
title: 'Vorgehensweise: Unterdrücken von Warnungen über das Menüelement | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
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
ms.openlocfilehash: be62471a950dc794bc3b9ff704cb187bbc943ce1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510377"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Gewusst wie: Unterdrücken von Warnungen über das Menüelement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [wie: Unterdrücken von Warnungen über das Menüelement](https://docs.microsoft.com/visualstudio/code-quality/how-to-suppress-warnings-by-using-the-menu-item).  
  
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



