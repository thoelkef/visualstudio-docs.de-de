---
title: "Beispiel für Excel-Erweiterung: TechnologyManager-Klasse | Microsoft-Dokumentation"
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
ms.openlocfilehash: 3493eff7352b49cc2a3b79300f7070d490354782
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-technologymanager-class"></a>Sample Excel Extension: TechnologyManager Class
Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>-Klasse und stellt Kerndiensten für die Erweiterung [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] bereit. Obwohl die Basisklasse über viele Methoden verfügt, wird in diesem Beispiel nur eine Teilmenge der Methoden verwendet.  
  
 Einige Methoden geben nur einen Eigenschaftswert zurück. Viele der Methoden ermöglichen es dem Entwickler, in das Modul für Tests der programmierten UI integrierte Standardalgorithmen zu überschreiben. Diese Methoden lösen eine Ausnahme des Typs <xref:System.NotSupportedException> aus oder geben `null` zurück, wodurch das Framework angewiesen wird, den Standardalgorithmus zu verwenden.  
  
 Abhängig von der Komplexität der zugrunde liegenden Technologie konnte die Entwicklung des Codes des Technologie-Managers einige Wochen, aber auch Monate in Anspruch nehmen. Excel bietet die Möglichkeit, einen potenziell sehr umfangreichen Technologie-Manager zu erstellen. Dieses Beispiel wurde bewusst auf Excel-Arbeitsblätter und -Zellen und die Verwendung einer eingeschränkten Formatierung begrenzt.  
  
 Nach Möglichkeit wird im Code des Technologie-Managers der von der `Communicator`-Klasse geöffnete .NET-Remotingkanal verwendet, um Informationen aus dem im Excel-Prozess ausgeführten Add-In zu extrahieren.  
  
## <a name="com-visibility"></a>COM-Sichtbarkeit  
 Beachten Sie, dass diese Klasse und alle Elementklassen, die die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>-Klasse erweitern, das Attribut <xref:System.Runtime.InteropServices.ComVisibleAttribute> mit dem Wert `true` aufweisen, das sicherstellt, dass die Klassen für COM sichtbar sind.  
  
## <a name="technologyname-property"></a>TechnologyName-Eigenschaft  
 Bei der Überschreibung der Eigenschaft <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName> muss ein eindeutiger und aussagekräftiger Name bereitgestellt werden, über den die zu Grunde liegende Technologie für jede andere Komponente der Erweiterung identifizierbar ist. Für diese Erweiterung ist der Wert „Excel“.  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel-Methode  
 Dieser Überschreibung der Methode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName> gibt eine Zahl zurück, die angibt, in welchem Maße der Technologie-Manager Unterstützung für das vom bereitgestellten Handler repräsentierte Steuerelement leisten kann. Je höher der zurückgegebene Wert, desto umfassender die Unterstützung des Technologie-Managers für das Steuerelement. In diesem Fall überprüft die Methode das Fenster mit dem Steuerelement und gibt den höchsten Wert zurück, wenn es sich um ein Excel-Arbeitsblatt handelt. Andernfalls wird 0 (null) zurückgegeben, was bedeutet, dass keine Unterstützung verfügbar ist.  
  
## <a name="methods-to-get-an-element"></a>Methoden zum Abrufen eines Elements  
 Es sind mehrere wichtige Methoden verfügbar, die vom Framework für den Test der programmierten UI verwendet werden, um ein spezifisches Element der Technologie oder ein Element einer anderen Technologie abzurufen, indem ein Handle (ein Punkt auf dem Bildschirm) bereitgestellt wird. Der Code für diese Methoden ist selbsterklärend. Folgende Basismethoden sind verfügbar:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## <a name="parsequeryid-method"></a>ParseQueryId-Methode  
 Beim Erstellen eines Tests der programmierten UI kann der Benutzer Eigenschaftswerte für einige oder alle Steuerelemente im Test angeben. Diese Eigenschaftswerte werden vom Testframework verwendet, um als Sucheigenschaften bezeichnete Name-Wert-Paare zu erstellen, mit deren Hilfe während des Tests nach bestimmten UI-Steuerelementen gesucht wird. Alle Sucheigenschaften zusammen bilden den Wert der Eigenschaft <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName> jedes Elements in der Technologie, einschließlich aller Steuerelemente. Da ein Steuerelement während eines Tests möglicherweise mehrmals gesucht werden muss, bietet diese Methode dem Technologie-Manager die Möglichkeit, die Analyse der Sucheigenschaften für das jeweilige Steuerelement zu optimieren. Diese Methode gibt auch ein Cookie zurück, das vom Framework für nachfolgende Suchen nach diesem Steuerelement verwendet werden kann. Bei der Implementierung der Methode werden die Sucheigenschaften mithilfe der Methode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName> analysiert.  
  
## <a name="matchelement-method"></a>MatchElement-Methode  
 Um mit dem Technologie-Manager eine Steuerelementsuche auszuführen, können sie die Methode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName> implementieren, damit entweder ein Array mögliche Treffer zurückgegeben oder eine Ausnahme vom Typ <xref:System.NotSupportedException> ausgelöst wird. So wird das Framework angewiesen, seinen eigenen Suchalgorithmus zu verwenden. In beiden Fällen müssen Sie die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>-Methode implementieren. Dies erfordert jedoch die Implementierung der Methode <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>.  
  
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
 [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
