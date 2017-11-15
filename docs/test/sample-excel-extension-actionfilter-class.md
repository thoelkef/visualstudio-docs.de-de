---
title: 'Sample Excel Extension: ActionFilter-Klasse | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: "11"
ms.author: douge
manager: douge
ms.openlocfilehash: 346cb9faddf2bd155c91d9fc72176020ba43197b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
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
