---
title: "Beispiel für Excel-Erweiterung: PropertyProvider-Klasse | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: "9"
ms.author: douge
manager: douge
ms.workload: multiple
ms.openlocfilehash: 7617b7aafac6c7345a94d0e792bc312c7e212e56
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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
