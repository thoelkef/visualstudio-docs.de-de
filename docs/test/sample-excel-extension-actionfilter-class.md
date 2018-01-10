---
title: 'Sample Excel Extension: ActionFilter-Klasse | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.author: gewarren
manager: ghogen
ms.workload: multiple
author: gewarren
ms.openlocfilehash: 8f2aa063163898a87ff563a356f6bb389cb07243
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-actionfilter-class"></a>Sample Excel Extension: ActionFilter Class
Diese interne Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>-Klasse und stellt einen Filter für Testaktionen auf einem [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Element dar.  
  
## <a name="simple-properties"></a>Einfache Eigenschaften  
 Durch diese schreibgeschützten Eigenschaften kann der Entwickler angeben, wie diese Testaktionsfilter vom Framework für den programmierten UI-Test ausgeführt werden. Die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>-Eigenschaft stellt z.B. den Namen des Aktionsfilters bereit. Andere Eigenschaften erhalten die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> des Aktionsfilters, den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> und den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>-Namen für die Testaktionen, die mithilfe diese Testaktionsfilters gefiltert werden. Andere stellen dar, ob <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A> angewendet wird und auch, ob die Testaktion <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A> ist.  
  
## <a name="processrule-method"></a>ProcessRule-Methode  
 Diese Methode wird vom Testframework der programmierten UI aufgerufen und führt den Filter für bereitgestellte <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> durch. Diese spezielle Überschreibung entfernt eine Mausklickaktion auf einer Zelle, wenn die nächste Aktion in der Liste Tastatureingaben an die Zelle sendet. Dann wird `false` zurückgegeben.  
  
## <a name="private-methods"></a>Private Methoden  
 Die `IsLeftClick`-Methode bestimmt, ob die angegebene Aktion einen Klick mit der linken Maustaste darstellt. Die `AreActionsOnSameExcelCell`-Methode bestimmt, ob zwei angegebene Aktionen auf der gleichen Zelle in Excel ausgeführt werden.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
