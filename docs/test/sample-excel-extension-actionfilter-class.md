---
title: "Sample Excel Extension: ActionFilter Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c69fe3c7-f797-4e90-b21c-f2cc4dddf152
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "mlearned"
manager: "douge"
---
# Sample Excel Extension: ActionFilter Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch diese interne Klasse wird die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>\-Klasse erweitert. Sie stellt einen Filter für Testaktionen für ein [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]\-Element dar.  
  
## Einfache Eigenschaften  
 Mithilfe dieser schreibgeschützten Eigenschaften kann der Entwickler angeben, wie dieser Testaktionsfilter vom Framework für den Test der codierten UI ausgeführt werden soll.  Die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Name%2A>\-Eigenschaft stellt z. B. den Namen des Aktionsfilters bereit.  Andere Eigenschaften rufen die <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Category%2A> des Aktionsfilters, den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.FilterType%2A> und den <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Group%2A>\-Namen der Testaktionen ab, die anhand dieses Testaktionsfilters gefiltert werden.  Andere geben an, ob ein Timeout angewendet werden soll \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.ApplyTimeout%2A>\) und ob die Testaktion aktiviert ist \(<xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter.Enabled%2A>\).  
  
## ProcessRule\-Methode  
 Diese Methode wird vom Framework für den Test der codierten UI aufgerufen und führt den Filter für den bereitgestellten <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack> aus.  Diese spezielle Überschreibung entfernt eine Maus aus Aktion in einer Zelle, wenn die nächste Aktion im Stapel Tastatureingaben an die Zelle sendet.  Dann wird `false` zurückgegeben.  
  
## Private\-Methoden  
 Durch die `IsLeftClick`\-Methode wird bestimmt, ob die bereitgestellte Aktion einen Klick mit der linken Maustaste darstellt.  Die `AreActionsOnSameExcelCell`\-Methode bestimmt, ob zwei bereitgestellte Aktionen in derselben Zelle in Excel ausgeführt werden.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.IUITestActionStack>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)