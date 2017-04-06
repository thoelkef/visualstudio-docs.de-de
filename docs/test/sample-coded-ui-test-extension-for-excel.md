---
title: "Sample Coded UI Test Extension for Excel (Beispielerweiterungen für programmierte UI-Test für Excel) | Microsoft-Dokumentation"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 13
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
ms.openlocfilehash: 46e8adfd4e4b66e743af8a0db5aecd3f40eb2de7
ms.lasthandoff: 04/04/2017

---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Sample Coded UI Test Extension for Excel
Die Erweiterungskomponente des Beispiels wird im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]Visual Studio.programmierten UI-Testprozess durchgeführt und ist in einer hierarchischen Beziehung mit der `ExtensionPackage`-Klasse an der Basis. Die `TechnologyManager`-, `ActionFilter`- und `PropertyProvider`-Klassen sind auf der nächsten Ebene, mit den Steuerelementen auf der obersten Ebene.  
  
 ![Testerweiterungsarchitektur für Excel](../test/media/excel_extarch.png "Excel_ExtArch")  
Erweiterungsarchitektur für Excel  
  
## <a name="extension-points"></a>Erweiterungspunkte  
 Diese Klassen stellen die Erweiterungspunkte dar, die in der Stichprobe implementiert werden, um programmierte UI-Tests für [!INCLUDE[ofprexcel](../test/includes/ofprexcel_md.md)] zu aktivieren.  
  
### <a name="extensionpackage"></a>ExtensionPackage  
 Geerbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>-Klasse. Dies ist der Einstiegspunkt für die Erweiterung der Tests der programmierten UI. Durch die Implementierung dieser abstrakten Klasse erhält das Framework für programmierte UI-Tests internen Zugriff auf Ihren benutzerdefinierten UI-Test-Technologie-Manager, UI-Test-Eigenschaftenanbieter und UI-Test-Aktionsfilter für das Testen der neuen UI. Weitere Informationen finden Sie unter [ExtensionPackage-Klasse](../test/sample-excel-extension-extensionpackage-class.md).  
  
### <a name="technologymanager"></a>TechnologyManager  
 Geerbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>-Klasse. Diese Klasse stellt einen Technologie-Manager für die Aufzeichnung und Wiedergabe des Tests zur Verfügung. Weitere Informationen finden Sie unter [TechnologyManager-Klasse](../test/sample-excel-extension-technologymanager-class.md).  
  
### <a name="actionfilter"></a>ActionFilter  
 Geerbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>-Klasse. Diese Klasse stellt eine Basisklasse für das Aggregieren ähnlicher Testaktionsergebnisse in ein einzelnes Testergebnis zur Verfügung. Weitere Informationen finden Sie unter [ActionFilter-Klasse](../test/sample-excel-extension-actionfilter-class.md).  
  
### <a name="technology-elements"></a>Technologieelemente  
 Eine Basisklasse geerbt von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>-Klasse bildet die Grundlage für die Technologieelemente Ihrer UI-Tests, die aufgezeichnet und wiedergegeben werden können. Weitere Informationen finden Sie unter [Elementklassen](../test/sample-excel-extension-element-classes.md).  
  
### <a name="propertyprovider"></a>PropertyProvider  
 Geerbt von der <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>-Klasse. Diese Klasse stellt eine Basisklasse für die Unterstützung der Eigenschaften von UI-Elementen für die Aufzeichnung und Wiedergabe der Tests bereit. Weitere Informationen finden Sie unter [PropertyProvider-Klasse](../test/sample-excel-extension-propertyprovider-class.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UITestActionFilter>   
 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>   
 [ExtensionPackage-Klasse](../test/sample-excel-extension-extensionpackage-class.md)   
 [TechnologyManager-Klasse](../test/sample-excel-extension-technologymanager-class.md)   
 [ActionFilter-Klasse](../test/sample-excel-extension-actionfilter-class.md)   
 [Elementklasse](../test/sample-excel-extension-element-classes.md)   
 [PropertyProvider-Klasse](../test/sample-excel-extension-propertyprovider-class.md)

