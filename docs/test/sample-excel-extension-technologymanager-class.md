---
title: "Beispiel für Excel-Erweiterung: TechnologyManager-Klasse | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
ms.author: douge
manager: douge
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 07e37b1a1d7b02992bb4da69bd158878095dd789
ms.lasthandoff: 04/04/2017

---
# <a name="sample-excel-extension-technologymanager-class"></a>Sample Excel Extension: TechnologyManager Class
Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>-Klasse und stellt Kerndienste für die [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Erweiterung bereit. Obwohl die Basisklasse über viele Methoden verfügt, wird in diesem Beispiel nur eine Teilmenge der Methoden verwendet.  
  
 Einige Methoden geben nur einen Eigenschaftswert zurück. Viele der Methoden ermöglichen es dem Entwickler, in das Modul für Tests der programmierten UI integrierte Standardalgorithmen zu überschreiben. Diese Methoden lösen eine <xref:System.NotSupportedException> aus oder aus oder geben `null` zurück, wodurch das Framework angewiesen wird, den Standardalgorithmus zu verwenden.  
  
 Abhängig von der Komplexität der zugrunde liegenden Technologie konnte die Entwicklung des Codes des Technologie-Managers einige Wochen, aber auch Monate in Anspruch nehmen. Excel bietet die Möglichkeit, einen potenziell sehr umfangreichen Technologie-Manager zu erstellen. Dieses Beispiel wurde bewusst auf Excel-Arbeitsblätter und -Zellen und die Verwendung einer eingeschränkten Formatierung begrenzt.  
  
 Nach Möglichkeit wird im Code des Technologie-Managers der von der `Communicator`-Klasse geöffnete .NET-Remotingkanal verwendet, um Informationen aus dem im Excel-Prozess ausgeführten Add-In zu extrahieren.  
  
## <a name="com-visibility"></a>COM-Sichtbarkeit  
 Diese Klasse und alle Elementklassen, die die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>-Klasse erweitern, verfügen über das <xref:System.Runtime.InteropServices.ComVisibleAttribute> mit dem Wert `true`, um sicherzustellen, dass die Klassen für COM sichtbar sind.  
  
## <a name="technologyname-property"></a>TechnologyName-Eigenschaft  
 Diese Überschreibung der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName>-Eigenschaft muss einen eindeutigen und aussagekräftigen Namen bereitstellen, der die zugrunde liegende Technologie für jede andere Komponente der Erweiterung identifiziert. Für diese Erweiterung ist der Wert „Excel“.  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel-Methode  
 Diese Überschreibung der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName>-Methode gibt eine Zahl zurück, die die Unterstützungsebene angibt, die der Technologie-Manager für das durch das bereitgestellte Handle dargestellte Steuerelement bieten kann. Je höher der zurückgegebene Wert, desto umfassender die Unterstützung des Technologie-Managers für das Steuerelement. In diesem Fall überprüft die Methode das Fenster mit dem Steuerelement und gibt den höchsten Wert zurück, wenn es sich um ein Excel-Arbeitsblatt handelt. Andernfalls wird 0 (null) zurückgegeben, was bedeutet, dass keine Unterstützung verfügbar ist.  
  
## <a name="methods-to-get-an-element"></a>Methoden zum Abrufen eines Elements  
 Es sind mehrere wichtige Methoden verfügbar, die vom Framework für den Test der programmierten UI verwendet werden, um ein spezifisches Element der Technologie oder ein Element einer anderen Technologie abzurufen, indem ein Handle (ein Punkt auf dem Bildschirm) bereitgestellt wird. Der Code für diese Methoden ist selbsterklärend. Folgende Basismethoden sind verfügbar:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId-Methode  
 Beim Erstellen eines Tests der programmierten UI kann der Benutzer Eigenschaftswerte für einige oder alle Steuerelemente im Test angeben. Diese Eigenschaftswerte werden vom Testframework verwendet, um als Sucheigenschaften bezeichnete Name-Wert-Paare zu erstellen, mit deren Hilfe während des Tests nach bestimmten UI-Steuerelementen gesucht wird. Zusammen stellen alle Sucheigenschaften den Wert der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName>-Eigenschaft aller Elemente in der Technologie dar, die jedes Steuerelement umfasst. Da ein Steuerelement während eines Tests möglicherweise mehrmals gesucht werden muss, bietet diese Methode dem Technologie-Manager die Möglichkeit, die Analyse der Sucheigenschaften für das jeweilige Steuerelement zu optimieren. Diese Methode gibt auch ein Cookie zurück, das vom Framework für nachfolgende Suchen nach diesem Steuerelement verwendet werden kann. Bei dieser Implementierung der Methode werden die Sucheigenschaften mithilfe der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>-Methode analysiert.  
  
## <a name="matchelement-method"></a>MatchElement-Methode  
 Um eine Steuerelementsuche mit dem Technologie-Manager auszuführen, können Sie die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName>-Methode implementieren, um entweder ein Array möglicher Übereinstimmungen zurückzugeben oder die <xref:System.NotSupportedException> auszulösen, wodurch das Framework angewiesen wird, seinen eigenen Suchalgorithmus zu verwenden. In beiden Fällen müssen Sie die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>-Methode implementieren, wobei wieder die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>-Methode verwendet wird.  
  
## <a name="navigation-methods"></a>Navigationsmethoden  
 Diese Methoden rufen das übergeordnete Element, untergeordnete Elemente oder gleichgeordnete Elemente des angegebenen Elements aus der Benutzeroberflächenhierarchie ab. Der Code ist einfach und mit verständlichen Kommentaren versehen.  
  
## <a name="getexcelelement-internal-method"></a>Interne GetExcelElement-Methode  
 Diese interne Methode akzeptiert ein Fensterhandle und Informationen zu einem Excel-Element und gibt das angeforderte Excel-Element zurück.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel (Erweitern von Tests der programmierten UI und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel)](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)

