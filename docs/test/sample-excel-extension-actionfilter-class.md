---
title: 'Sample Excel Extension: ActionFilter-Klasse | Microsoft-Dokumentation'
ms.date: 11/04/2016
ms.technology: vs-ide-test
ms.topic: conceptual
ms.author: gewarren
manager: douge
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 6f98afa819fceb4f8b8b34d5aa268f11f7b16993
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Sample Excel Extension: ActionFilter Class

Diese interne Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>-Klasse und stellt einen Filter für Testaktionen auf einem [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Element dar.

## <a name="simple-properties"></a>Einfache Eigenschaften

Durch diese schreibgeschützten Eigenschaften wird angegeben, wie der Testaktionsfilter vom Framework für den programmierten UI-Test ausgeführt werden soll. Die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>-Eigenschaft stellt z.B. den Namen des Aktionsfilters bereit. Andere Eigenschaften erhalten die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> des Aktionsfilters, den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> und den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>-Namen für die Testaktionen, die mithilfe diese Testaktionsfilters gefiltert werden. Andere stellen dar, ob <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> angewendet wird und auch, ob die Testaktion <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A> ist.

## <a name="processrule-method"></a>ProcessRule-Methode

Diese Methode wird vom Testframework der programmierten UI aufgerufen und führt den Filter für bereitgestellte <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> durch. Diese spezielle Überschreibung entfernt eine Mausklickaktion auf einer Zelle, wenn die nächste Aktion in der Liste Tastatureingaben an die Zelle sendet. Dann wird `false` zurückgegeben.

## <a name="private-methods"></a>Private Methoden

Die `IsLeftClick`-Methode bestimmt, ob die angegebene Aktion einen Klick mit der linken Maustaste darstellt. Die `AreActionsOnSameExcelCell`-Methode bestimmt, ob zwei angegebene Aktionen auf der gleichen Zelle in Excel ausgeführt werden.

## <a name="see-also"></a>Siehe auch

- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>
- [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
