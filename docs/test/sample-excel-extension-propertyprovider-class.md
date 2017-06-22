---
title: "Beispiel für Excel-Erweiterung: PropertyProvider-Klasse | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: 99397f8f0c6e0e261451cae642cf6e48fe5bba56
ms.contentlocale: de-de
ms.lasthandoff: 05/19/2017

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

