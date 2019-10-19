---
title: 'Gewusst wie: Unterdrücken von Warnungen über das Menü Element | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- warnings, suppressing
- code analysis, suppressing warnings
ms.assetid: 36bd1850-dcde-4ed0-9bc3-0b83df434362
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 96b7433ff4f696989142aa2c2ce47982006b93b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72610011"
---
# <a name="how-to-suppress-warnings-by-using-the-menu-item"></a>Gewusst wie: Unterdrücken von Warnungen über das Menüelement
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

HINWEIS]
> Bei der Quell Unterdrückung wird für Website Projekte nicht unterstützt.

 Sie können das Fenster "Code Analyse" verwenden, um Code Analyse Warnungen zu unterdrücken. Das unterdrücken einer Warnung ist nicht identisch mit der Deaktivierung. Wenn Sie eine Warnung unterdrücken, gilt sie nur für eine bestimmte Instanz des Verstoßes. Andere Verstöße gegen dieselbe Warnung werden weiterhin im Fehlerliste Fenster gemeldet.

 Nachdem Sie die Code Analyse ausgeführt haben, können Sie feststellen, dass mindestens eine der Code Analyse Warnungen, die im Code Analysefenster angezeigt werden, nicht auf die Anwendung anwendbar ist. Beispielsweise können Sie feststellen, dass der Code unverändert ist. Oder es kann vorkommen, dass einige Verstöße eine niedrige Priorität haben und im aktuellen Entwicklungs Durchlauf nicht korrigiert werden. Unabhängig von der Ursache ist es häufig hilfreich, anzugeben, dass die Warnung nicht anwendbar ist, damit die Teammitglieder wissen, dass der Code überprüft wurde und dass die Warnung unterdrückt werden konnte. In der Quellen Unterdrückung ist nützlich, da Sie eine Unterdrückung in der Nähe der Warnung platzieren können, in der die Warnung generiert wird.

 Sie können auswählen, ob die Unterdrückung im Quellcode oder in der globalen Unterdrückungs Datei angezeigt werden soll. Einige Unterdrückungen müssen in die globale Unterdrückungs Datei eingefügt werden. Wenn dies der Fall ist, wird die Option **in der Quelle** deaktiviert.

### <a name="to-suppress-a-warning-by-using-menu-item"></a>So unterdrücken Sie eine Warnung mithilfe eines Menü Elements

1. Wählen Sie im Menü **analysieren** die Option **Fenster** aus, und wählen Sie dann **Code Analyse**aus.

2. Wählen Sie im Fenster " **Code Analyse** " die Warnung unterdrücken aus.

3. Wählen Sie Aktionen und dann **Nachricht unterdrücken**aus, und wählen Sie dann entweder **in Quelle** oder **in Projekt Unterdrückungs Datei**aus.

     Die jeweilige Warnung wird unterdrückt, und die Warnung wird im Code Analysefenster mit einem durchgestrichen angezeigt.

> [!NOTE]
> Unterdrückungen ohne Ziel werden in der globalen Unterdrückungs Datei angezeigt.
