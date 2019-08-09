---
title: 'Beispiel für Excel-Erweiterung: Aktionfilter-Klasse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 13
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 26eb001de3a8fed7c6bb1d9d1a547aa618e745e8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/09/2019
ms.locfileid: "68871606"
---
# <a name="sample-excel-extension-actionfilter-class"></a>Beispiel für Excel-Erweiterung: ActionFilter-Klasse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese interne Klasse erweitert die [uitestaktionfilter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) -Klasse und stellt einen Filter für Test Aktionen auf [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] einem-Element dar.

## <a name="simple-properties"></a>Einfache Eigenschaften
 Durch diese schreibgeschützten Eigenschaften kann der Entwickler angeben, wie diese Testaktionsfilter vom Framework für den programmierten UI-Test ausgeführt werden. Die `UITestActionFilter.Name`-Eigenschaft stellt z.B. den Namen des Aktionsfilters bereit. Andere Eigenschaften erhalten die `UITestActionFilter.Category` des Aktionsfilters, den `UITestActionFilter.FilterType` und den `UITestActionFilter.Group`-Namen für die Testaktionen, die mithilfe diese Testaktionsfilters gefiltert werden. Andere stellen dar, ob `UITestActionFilter.ApplyTimeout` angewendet wird und auch, ob die Testaktion `UITestActionFilter.Enabled` ist.

## <a name="processrule-method"></a>ProcessRule-Methode
 Diese Methode wird vom Testframework der programmierten UI aufgerufen und führt den Filter für bereitgestellte `IUITestActionStack` durch. Diese spezielle Überschreibung entfernt eine Mausklickaktion auf einer Zelle, wenn die nächste Aktion in der Liste Tastatureingaben an die Zelle sendet. Dann wird `false` zurückgegeben.

## <a name="private-methods"></a>Private Methoden
 Die `IsLeftClick`-Methode bestimmt, ob die angegebene Aktion einen Klick mit der linken Maustaste darstellt. Die `AreActionsOnSameExcelCell`-Methode bestimmt, ob zwei angegebene Aktionen auf der gleichen Zelle in Excel ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
