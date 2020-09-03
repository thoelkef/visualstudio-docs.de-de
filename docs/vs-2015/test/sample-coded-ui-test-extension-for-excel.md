---
title: Sample Coded UI Test Extension for Excel (Beispielerweiterungen für programmierte UI-Test für Excel) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, extensions for Excel
ms.assetid: 451e4d14-7fac-42f9-af56-2bdc8414c6c7
caps.latest.revision: 15
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e0c6075f9f95f7dc1d21db91936cf35c76f9b2e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672226"
---
# <a name="sample-coded-ui-test-extension-for-excel"></a>Beispielerweiterung für Tests der programmierten Benutzeroberfläche für Excel
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Erweiterungskomponente des Beispiels wird im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Visual Studio.programmierten UI-Testprozess durchgeführt und ist in einer hierarchischen Beziehung mit der `ExtensionPackage`-Klasse an der Basis. Die `TechnologyManager`-, `ActionFilter`- und `PropertyProvider`-Klassen sind auf der nächsten Ebene, mit den Steuerelementen auf der obersten Ebene.

 ![Excel-Test Erweiterungs Architektur](../test/media/excel-extarch.png "Excel_ExtArch") Excel-Erweiterungs Architektur

## <a name="extension-points"></a>Erweiterungspunkte
 Diese Klassen stellen die Erweiterungspunkte dar, die in der Stichprobe implementiert werden, um programmierte UI-Tests für [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] zu aktivieren.

### <a name="extensionpackage"></a>ExtensionPackage
 Von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>-Klasse geerbt. Dies ist der Einstiegspunkt für die Erweiterung für den Test der programmierten UI. Durch die Implementierung dieser abstrakten Klasse erhält das Framework für programmierte UI-Tests internen Zugriff auf Ihren benutzerdefinierten UI-Test-Technologie-Manager, UI-Test-Eigenschaftenanbieter und UI-Test-Aktionsfilter für das Testen der neuen UI. Weitere Informationen finden Sie unter [ExtensionPackage-Klasse](../test/sample-excel-extension-extensionpackage-class.md).

### <a name="technologymanager"></a>TechnologyManager
 Von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyManager>-Klasse geerbt. Diese Klasse stellt einen Technologie-Manager für die Testaufzeichnung und -wiedergabe bereit. Weitere Informationen finden Sie unter [TechnologyManager-Klasse](../test/sample-excel-extension-technologymanager-class.md).

### <a name="actionfilter"></a>ActionFilter
 Diese Klasse wird von der [UITestAction Filter](/previous-versions/visualstudio/visual-studio-2012/dd985757(v=vs.110)) -Klasse geerbt. diese Klasse stellt eine Basisklasse zum aggregierten von ähnlichen Test Aktions Ergebnissen in einem einzelnen Testergebnis bereit. Weitere Informationen finden Sie unter [ActionFilter-Klasse](../test/sample-excel-extension-actionfilter-class.md).

### <a name="technology-elements"></a>Technologieelemente
 Eine von der <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>-Klasse geerbte Basisklasse stellt die Grundlage für die Technologieelemente Ihrer UI-Tests bereit, die aufgezeichnet und wiedergegeben werden können. Weitere Informationen finden Sie unter [Elementklassen](../test/sample-excel-extension-element-classes.md).

### <a name="propertyprovider"></a>PropertyProvider
 Von der <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>-Klasse geerbt. Diese Klasse stellt eine Basisklasse für die Unterstützung der Eigenschaften von UI-Elementen für die Aufzeichnung und Wiedergabe der Tests bereit. Weitere Informationen finden Sie unter [PropertyProvider-Klasse](../test/sample-excel-extension-propertyprovider-class.md).

## <a name="see-also"></a>Weitere Informationen

- <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestPropertyProvider>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>
- <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITestExtensionPackage>
- [ExtensionPackage-Klasse](../test/sample-excel-extension-extensionpackage-class.md)
- [TechnologyManager-Klasse](../test/sample-excel-extension-technologymanager-class.md)
- [ActionFilter-Klasse](../test/sample-excel-extension-actionfilter-class.md)
- [Elementklassen](../test/sample-excel-extension-element-classes.md)
- [PropertyProvider-Klasse](../test/sample-excel-extension-propertyprovider-class.md)
