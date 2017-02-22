---
title: "Beispiel f&#252;r Excel-Erweiterung: PropertyProvider-Klasse | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "mlearned"
manager: "douge"
---
# Beispiel f&#252;r Excel-Erweiterung: PropertyProvider-Klasse
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Diese interne Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>\-Klasse und stellt Eigenschaftendienste für [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]\-Elemente zur Aufzeichnung und Wiedergabe von Tests der Benutzeroberfläche bereit.  
  
## GetControlSupportLevel\-Methode  
 Von der <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A>\-Methode wird eine Zahl zurückgegeben, die die Ebene der Unterstützung angibt, die der Eigenschaftenanbieter für das bereitgestellte Steuerelement anbieten kann.  Je höher der zurückgegebene Wert ist, desto umfassender ist die Unterstützung des Eigenschaftenanbieters für das Steuerelement.  In diesem Fall wird von der Methode der Wert der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A>\-Eigenschaft des bereitgestellten Steuerelements überprüft.  Wenn der Wert "Excel" lautet und <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> angibt, dass es sich um ein `CellElement` handelt, wird von der Methode der höchste Wert zurückgegeben. Andernfalls wird 0 \(Null\) zurückgegeben, was bedeutet, dass keine Unterstützung verfügbar ist.  
  
## GetPropertyNames\-Methode  
 Gibt ein Wörterbuch der Eigenschaftennamen und Eigenschaftendeskriptoren für die unterstützten Eigenschaften eines Steuerelements für Excel\-Zellen zurück.  
  
## GetPropertyDescriptor\-Methode  
 Diese Methode wird vom Testframework aufgerufen, um den vordefinierten Eigenschaftendeskriptor für den angegebenen Eigenschaftennamen abzurufen.  
  
## GetPropertyValue\-Methode und SetPropertyValue\-Methode  
 Von der `GetPropertyValue`\-Methode wird der Eigenschaftswert aus Excel mithilfe der `Communicator`\-Klasse dieser Erweiterung zurückgegeben.  Von der `SetPropertyValue`\-Methode wird der Eigenschaftswert mithilfe der <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>\-Klasse und der `Communicator`\-Komponente festgelegt.  Diese Methoden werden vom Testframework aufgerufen.  
  
## Anpassungsmethoden für die Codegenerierung  
 Diese Methoden werden nicht für diese Erweiterung implementiert.  Daher geben sie entweder `null` zurück oder lösen <xref:System.NotImplementedException> aus.  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Extending Coded UI Tests and Action Recordings to Support Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)