---
title: 'Beispiel für Excel-Erweiterung: PropertyProvider-Klasse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 075d9b8d-8658-4fca-8711-08304dbac1c5
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8ae254f85b00c47ba00250641f7afe0a638ceabc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660426"
---
# <a name="sample-excel-extension-propertyprovider-class"></a>Beispiel für Excel-Erweiterung: PropertyProvider-Klasse
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese interne Klasse erweitert die <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>-Klasse und stellt Eigenschaftendienste für [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]-Elemente zur Aufzeichnung und Wiedergabe von Tests Benutzeroberfläche bereit.

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

## <a name="see-also"></a>Weitere Informationen
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider> <xref:Microsoft.VisualStudio.TestTools.UITesting.Keyboard>
 [Erweitern von Tests der codierten UI-Tests und Aktionsaufzeichnungen zur Unterstützung von Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
