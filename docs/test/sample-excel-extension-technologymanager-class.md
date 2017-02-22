---
title: "Sample Excel Extension: TechnologyManager Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8a7b760d-b5ac-4451-9593-6ac1a0b95cdb
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Sample Excel Extension: TechnologyManager Class
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>\-Klasse und stellt Kerndienste für die [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]\-Erweiterung bereit.  Obwohl die Basisklasse über viele Methoden verfügt, wird in diesem Beispiel nur eine Teilmenge der Methoden verwendet.  
  
 Einige Methoden geben nur einen Eigenschaftswert zurück.  Viele der Methoden ermöglichen es dem Entwickler, in das Modul für Tests der codierten UI integrierte Standardalgorithmen zu überschreiben.  Diese Methoden lösen eine <xref:System.NotSupportedException> aus oder geben `null` zurück, wodurch das Framework angewiesen wird, den Standardalgorithmus zu verwenden.  
  
 Abhängig von der Komplexität der zugrunde liegenden Technologie konnte die Entwicklung des Codes des Technologie\-Managers einige Wochen, aber auch Monate in Anspruch nehmen.  Excel bietet eine Möglichkeit, einen potenziell sehr umfangreichen Technologie\-Manager zu erstellen.  Dieses Beispiel wurde bewusst auf Excel\-Arbeitsblatter und \-Zellen und die Verwendung einer eingeschränkten Formatierung begrenzt.  
  
 Nach Möglichkeit wird im Code des Technologie\-Managers der von der `Communicator`\-Klasse geöffnete .NET\-Remotingkanal verwendet, um Informationen aus dem im Excel\-Prozess ausgeführten Add\-In zu extrahieren.  
  
## COM\-Sichtbarkeit  
 Diese Klasse und alle Elementklassen, die die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>\-Klasse erweitern, verfügen über das <xref:System.Runtime.InteropServices.ComVisibleAttribute> mit dem Wert `true`. Dadurch wird sichergestellt, dass die Klassen für COM sichtbar sind.  
  
## TechnologyName\-Eigenschaft  
 Diese Überschreibung der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.TechnologyName%2A?displayProperty=fullName>\-Eigenschaft muss einen eindeutigen und aussagekräftigen Namen bereitstellen, der die zugrunde liegende Technologie für jede andere Komponente der Erweiterung identifiziert.  Für diese Erweiterung lautet der Wert "Excel".  
  
## GetControlSupportLevel\-Methode  
 Diese Überschreibung der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetControlSupportLevel%2A?displayProperty=fullName>\-Methode gibt eine Zahl zurück, die die Unterstützungsebene angibt, die der Technologie\-Manager für das durch das bereitgestellte Handle dargestellte Steuerelement bieten kann.  Je höher der zurückgegebene Wert ist, desto umfassender ist die Unterstützung des Technologie\-Managers für das Steuerelement.  In diesem Fall überprüft die Methode das Fenster mit dem Steuerelement und gibt den höchsten Wert zurück, wenn es sich um ein Excel\-Arbeitsblatt handelt. Andernfalls wird 0 \(Null\) zurückgegeben, was bedeutet, dass keine Unterstützung verfügbar ist.  
  
## Methoden zum Abrufen eines Elements  
 Es sind mehrere wichtige Methoden verfügbar, die vom Framework für den Test der codierten UI verwendet werden, um ein spezifisches Element der Technologie oder ein Element einer anderen Technologie abzurufen, indem ein Handle \(ein Punkt auf dem Bildschirm\) bereitgestellt wird.  Der Code für diese Methoden ist ohne Erläuterung verständlich.  Folgende Basismethoden stehen zur Verfügung:  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetFocusedElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromPoint%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromWindowHandle%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.GetElementFromNativeElement%2A?displayProperty=fullName>  
  
-   <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.ConvertToThisTechnology%2A?displayProperty=fullName>  
  
## ParseQueryId\-Methode  
 Beim Erstellen eines Tests der codierten UI kann der Benutzer Eigenschaftswerte für einige oder alle Steuerelemente im Test angeben.  Diese Eigenschaftswerte werden vom Testframework verwendet, um als Sucheigenschaften bezeichnete Name\-Wert\-Paare zu erstellen, mit deren Hilfe während des Tests nach bestimmten UI\-Steuerelementen gesucht wird.  Zusammen stellen alle Sucheigenschaften den Wert der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A?displayProperty=fullName>\-Eigenschaft aller Elemente in der Technologie dar, die jedes Steuerelement umfasst.  Da ein Steuerelement während eines Tests möglicherweise mehrmals gesucht werden muss, bietet diese Methode dem Technologie\-Manager die Möglichkeit, die Analyse der Sucheigenschaften für das jeweilige Steuerelement zu optimieren.  Diese Methode gibt auch ein Cookie zurück, das vom Framework für nachfolgende Suchen nach diesem Steuerelement verwendet werden kann.  Bei dieser Implementierung der Methode werden die Sucheigenschaften mithilfe der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>\-Methode analysiert.  
  
## MatchElement\-Methode  
 Um eine Steuerelementsuche mit dem Technologie\-Manager auszuführen, können Sie die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.Search%2A?displayProperty=fullName>\-Methode implementieren, um entweder ein Array möglicher Übereinstimmungen zurückzugeben oder die <xref:System.NotSupportedException> auszulösen, wodurch das Framework angewiesen wird, seinen eigenen Suchalgorithmus zu verwenden.  In beiden Fällen müssen Sie die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager.MatchElement%2A>\-Methode implementieren, wobei wieder die <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.AndCondition.Match%2A?displayProperty=fullName>\-Methode verwendet wird.  
  
## Navigationsmethoden  
 Diese Methoden rufen das übergeordnete Element, untergeordnete Elemente oder gleichgeordnete Elemente des angegebenen Elements aus der Benutzeroberflächenhierarchie ab.  Der Code ist einfach und mit verständlichen Kommentaren versehen.  
  
## Interne GetExcelElement\-Methode  
 Diese interne Methode akzeptiert ein Fensterhandle und Informationen zu einem Excel\-Element und gibt das angeforderte Excel\-Element zurück.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>   
 <xref:System.NotSupportedException>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:System.Runtime.InteropServices.ComVisibleAttribute>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)