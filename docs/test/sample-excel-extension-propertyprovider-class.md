---
title: "Beispiel für Excel-Erweiterung: PropertyProvider-Klasse | Microsoft-Dokumentation"
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
ms.openlocfilehash: d1383398e245b6e6317ccbbf9c981e199b793e1a
ms.sourcegitcommit: 7ae502c5767a34dc35e760ff02032f4902c7c02b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/09/2018
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Beispiel für Excel-Erweiterung: PropertyProvider-Klasse
Diese interne Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>-Klasse und stellt Eigenschaftendienste für [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)]-Elemente zur Aufzeichnung und Wiedergabe von Tests Benutzeroberfläche bereit.  
  
## <a name="getcontrolsupportlevel-method"></a>GetControlSupportLevel-Methode  
 Die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider.GetControlSupportLevel%2A>-Methode gibt eine Zahl zurück, die die Unterstützungsebene angibt, die Eigenschaftenanbieter für das bereitgestellte Steuerelement anbieten können. Je höher der zurückgegebene Wert, desto umfassender die Unterstützung des Eigenschaftenanbieters für das Steuerelement. In diesem Fall prüft die Methode den Wert der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.TechnologyName%2A>-Eigenschaft des dargestellten Steuerelements. Wenn der Wert „Excel“ lautet und <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IUITechnologyElement.ControlTypeName%2A> angibt, dass es sich um ein `CellElement` handelt, wird von der Methode der höchste Wert zurückgegeben. Andernfalls wird 0 (null) zurückgegeben, was bedeutet, dass keine Unterstützung verfügbar ist.  
  
## <a name="getpropertynames-method"></a>GetPropertyNames-Methode  
 Gibt ein Wörterbuch der Eigenschaftennamen und Eigenschaftendeskriptoren für die unterstützten Eigenschaften eines Steuerelements für Excel-Zellen zurück.  
  
## <a name="getpropertydescriptor-method"></a>GetPropertyDescriptor-Methode  
 Diese Methode wird vom Testframework aufgerufen, um den vordefinierten Eigenschaftendeskriptor für den angegebenen Eigenschaftennamen abzurufen.  
  
## <a name="getpropertyvalue-and-setpropertyvalue-methods"></a>GetPropertyValue und SetPropertyValue-Methode  
 Die `GetPropertyValue`-Methode gibt den Eigenschaftswert aus Excel mithilfe der `Communicator`-Klasse dieser Erweiterung zurück. Die `SetPropertyValue`-Methode verwendet die <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>-Klasse und die `Communicator`-Komponente, um den Eigenschaftswert festzulegen. Diese Methoden werden vom Testframework aufgerufen.  
  
## <a name="code-generation-customization-methods"></a>Anpassungsmethoden für die Codegenerierung  
 Diese Methoden sind nicht für diese Erweiterung implementiert. Deshalb geben Sie entweder `null` zurück oder lösen <xref:System.NotImplementedException> aus.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>   
 [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
