---
title: "Zusammenführen von XML in Funktions- und Paketmanifesten | Microsoft Docs"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: SharePoint development in Visual Studio, packaging
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: "10"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6d418e757a93d77b0034bbdb8287b0e81a5a3860
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="merging-xml-in-feature-and-package-manifests"></a>Zusammenführen von XML in Funktions- und Paketmanifesten
  Funktionen und Pakete werden durch definiert [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifestdateien. Diese App Manifeste sind eine Kombination von Designern und benutzerdefinierte generierte Daten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in der Manifestdatei Vorlage vom Benutzer eingegeben. Zum Zeitpunkt der Verpackung [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt die benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Anweisungen mit der vom Designer bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] bilden die gepackte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifestdatei. Ähnliche Elemente mit den Ausnahmen, die weiter unten in der Merge-Ausnahmen werden zusammengeführt, um zu vermeiden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Validierungsfehler, nachdem Sie die Dateien in SharePoint bereitstellen, stellen das Manifest Dateien kleiner und effizienter.  
  
## <a name="modifying-the-manifests"></a>Ändern die Manifeste  
 Die gepackten Manifestdateien kann nicht direkt geändert werden, bis Sie das Feature oder Paket-Designer deaktivieren. Können jedoch benutzerdefinierte manuell hinzufügen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente, die das manifest Vorlage entweder über die Funktion und Paket-Designer oder der [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Weitere Informationen finden Sie unter [wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md) und [wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Funktions- und Manifest Mergeprozess  
 Wenn Sie zusammen mit Designer bereitgestellte Elemente, benutzerdefinierte Elemente kombinieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] folgenden Prozess verwendet. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]überprüft, ob jedes Element einen eindeutigen Schlüsselwert verfügt. Wenn ein Element keine eindeutigen Schlüsselwert verfügt, wird es in der App-Manifestdatei angefügt. Elemente mit mehreren Schlüsseln können auf ähnliche Weise können nicht zusammengeführt werden. Aus diesem Grund werden sie in die Manifestdatei angefügt.  
  
 Wenn ein Element einen eindeutigen Schlüssel, dessen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vergleicht die Werte des Designers und benutzerdefinierte Schlüssel. Wenn die Werte übereinstimmen, führen sie in einen einzelnen Wert. Wenn die Werte unterscheiden, die Designer-Schlüsselwert wird verworfen, und der benutzerdefinierte Schlüssel-Wert dient. Sammlungen werden ebenfalls zusammengeführt. Beispielsweise, wenn vom Designer generierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] und das benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] sowohl eine Auflistung von Assemblys enthalten, das App-Manifest enthält nur eine Auflistung von Assemblys.  
  
## <a name="merge-exceptions"></a>Zusammenführen von Ausnahmen  
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]führt die meisten Designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente zusammen mit ähnlichen benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente so lange, wie sie ein einzelnes, eindeutigen identifizierendes Attribut verfügen. Einige Elemente fehlen jedoch den eindeutigen Bezeichner für die erforderlichen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zusammenführen. Diese Elemente werden als bezeichnet *merge Ausnahmen*. In diesen Fällen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht die benutzerdefinierte zusammen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente zusammen mit der vom Designer bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente, sondern stattdessen in der App-Manifestdatei angefügt.  
  
 Es folgt eine Liste der Merge-Ausnahmen für Funktions- und [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifestdateien.  
  
|Designer|XML-Element|  
|--------------|-----------------|  
|Funktions-designer|ActivationDependency|  
|Funktions-designer|UpgradeAction|  
|Paket-designer|SafeControl|  
|Paket-designer|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Elemente von Manifesten Funktion  
 In der folgenden Tabelle ist eine Liste aller manifest Feature-Elemente, die zusammengeführt werden können und ihre eindeutige Schlüssel, für den Abgleich verwendet wird.  
  
|Elementname|Eindeutige Schlüssel|  
|------------------|----------------|  
|Feature (alle Attribute)|*Attributname* (jeder Attributname des Feature-Elements ist ein eindeutiger Schlüssel.)|  
|ElementFile|Speicherort|  
|ElementManifests/ElementManifest|Speicherort|  
|Properties-Eigenschaft|Key|  
|CustomUpgradeAction|Name|  
|CustomUpgradeActionParameter|Name|  
  
> [!NOTE]  
>  Da die einzige Möglichkeit zum Ändern der CustomUpgradeAction-Element in der benutzerdefinierten ist [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Editor, die Auswirkungen der Zusammenführung nicht von ist zu niedrig.  
  
## <a name="package-manifest-elements"></a>Paket-Manifest-Elemente  
 In der folgenden Tabelle ist eine Liste aller manifest Paketelemente, die zusammengeführt werden können und ihre eindeutige Schlüssel, für den Abgleich verwendet wird.  
  
|Elementname|Eindeutige Schlüssel|  
|------------------|----------------|  
|Lösung (alle Attribute)|*Attributname* (jeder Attributname des Elements Lösung ist ein eindeutiger Schlüssel.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Speicherort|  
|Assemblys-Assembly|Speicherort|  
|ClassResources/ClassResource|Speicherort|  
|DwpFiles/DwpFile|Speicherort|  
|FeatureManifests/FeatureManifest|Speicherort|  
|Ressourcen und Ressourcen|Speicherort|  
|RootFiles/RootFile|Speicherort|  
|SiteDefinitionManifests/SiteDefinitionManifest|Speicherort|  
|WebTempFile|Speicherort|  
|TemplateFiles/TemplateFile|Speicherort|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Manuelles Hinzufügen von bereitgestellten Dateien  
 Einige Elemente von Manifesten, z. B. ApplicationResourceFile und DwpFiles, geben Sie einen Speicherort, der einen Dateinamen enthält. Allerdings ist einen Eintrag für Datei der manifest-Vorlage die zugrunde liegende Datei für das Paket hinzufügen nicht. Sie müssen die Datei hinzufügen, um das Projekt in das Paket eingeschlossen wird und durch das Festlegen der Eigenschaft Deployment Type wird entsprechend.  
  
## <a name="see-also"></a>Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Projektmappen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  