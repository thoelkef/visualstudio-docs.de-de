---
title: Zusammenführen von XML in Funktions- und Paketmanifesten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, packaging
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: d3101245d720e9fdd1c4923ea03acd5b2d4db816
ms.sourcegitcommit: d9e4ea95d0ea70827de281754067309a517205a1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2018
ms.locfileid: "37119175"
---
# <a name="merge-xml-in-feature-and-package-manifests"></a>Zusammenführen von XML in Funktions- und Manifesten
  Funktionen und Pakete werden durch definiert [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifestdateien. Diese App-Pakete Manifeste sind eine Kombination von Daten aus Designer und benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] in der Manifestvorlage vom Benutzer eingegeben. Zum Zeitpunkt der paketerstellung [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt die benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Anweisungen mit der vom Designer bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Paket bilden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] manifest-Datei. Ähnliche Elemente, mit der Ausnahmen, die weiter unten in der Merge-Ausnahmen werden zusammengeführt, um zu vermeiden [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Validierungsfehler, nachdem Sie die Dateien in SharePoint bereitstellen, und das Manifest zu kleiner und effizienter Dateien.  
  
## <a name="modify-the-manifests"></a>Ändern Sie die Manifeste
 Sie können die Paket-Manifesten-Dateien nicht direkt ändern, bis Sie die Funktion oder ein Paket-Designer deaktivieren. Können jedoch benutzerdefinierte manuell hinzufügen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elementen, die die Manifestvorlage entweder über die Funktion und Paket-Designer oder dem [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Editor. Weitere Informationen finden Sie unter [wie: Anpassen eines SharePoint-Features](../sharepoint/how-to-customize-a-sharepoint-feature.md) und [wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## <a name="feature-and-package-manifest-merge-process"></a>Funktions- und manifest Mergeprozess
 Wenn Sie benutzerdefinierte Elemente mit Elementen bereitgestellten Designer, kombinieren [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] verwendet folgendes Verfahren. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] überprüft, ob jedes Element einen eindeutigen Schlüsselwert verfügt. Wenn ein Element keine eindeutigen Schlüsselwert verfügt, wird es in die Manifestdatei für gepackte angefügt. Elemente, die mehrere Schlüssel können auf ähnliche Weise können nicht zusammengeführt werden. Aus diesem Grund werden sie an der manifest-Datei angefügt.  
  
 Wenn ein Element einen eindeutigen Schlüssel, verfügt über [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] vergleicht die Werte des Designers und benutzerdefinierte Schlüssel. Wenn die Werte übereinstimmen, führen sie in einem einzelnen Wert. Wenn die Werte voneinander abweichen, die Designer-Schlüssel-Wert verworfen und der benutzerdefinierte Schlüssel-Wert wird verwendet. Sammlungen werden ebenfalls zusammengeführt. Beispielsweise, wenn vom Designer generierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] und das benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] beide enthalten eine Auflistung von Assemblys, die Paket-Manifest enthält nur eine Auflistung von Assemblys.  
  
## <a name="merge-exceptions"></a>Zusammenführen von Ausnahmen
 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] führt die meisten Designer [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente mit ähnlichen benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente, die so lange, wie sie ein einzige, eindeutige, identifizierende Attribut haben. Einige Elemente fehlen allerdings den eindeutigen Bezeichner für die erforderlichen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zusammenführen. Diese Elemente werden als bezeichnet *merge Ausnahmen*. In diesen Fällen [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ist nicht die benutzerdefinierte zusammenführen [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] zusammen mit der vom Designer bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Elemente, sondern stattdessen in die Manifestdatei für gepackte angefügt.  
  
 Es folgt eine Liste der Merge-Ausnahmen für Funktions- und [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] Manifestdateien.  
  
|Designer|XML-Element|  
|--------------|-----------------|  
|Funktions-designer|ActivationDependency|  
|Funktions-designer|UpgradeAction|  
|Paket-designer|SafeControl|  
|Paket-designer|CodeAccessSecurity|  
  
## <a name="feature-manifest-elements"></a>Manifest Funktionselemente
 In der folgende Tabelle ist eine Liste mit Manifesten alle Feature-Elemente, die zusammengeführt werden können und ihre eindeutigen Schlüssel, der für den Abgleich verwendet wird.  
  
|Elementname|Eindeutiger Schlüssel|  
|------------------|----------------|  
|Feature (alle Attribute)|*Attributname* (jeder Attributname des "das Feature"-Element ist ein eindeutiger Schlüssel.)|  
|ElementFile|Speicherort|  
|ElementManifests/ElementManifest|Speicherort|  
|Properties-Eigenschaft|Key|  
|CustomUpgradeAction|name|  
|CustomUpgradeActionParameter|name|  
  
> [!NOTE]  
>  Da die einzige Möglichkeit zum Ändern der CustomUpgradeAction-Element in der benutzerdefinierten ist [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)] -Editor, die Auswirkungen der Zusammenführung nicht ist zu niedrig.  
  
## <a name="package-manifest-elements"></a>Paket-manifest-Elemente
 In der folgende Tabelle ist eine Liste mit allen manifest Paketelemente, die zusammengeführt werden können und ihre eindeutigen Schlüssel, der für den Abgleich verwendet wird.  
  
|Elementname|Eindeutiger Schlüssel|  
|------------------|----------------|  
|Projektmappen (alle Attribute)|*Attributname* (jeder Attributname des Solution-Element ist ein eindeutiger Schlüssel.)|  
|ApplicationResourceFiles/ApplicationResourceFile|Speicherort|  
|Assemblys/Assembly|Speicherort|  
|ClassResources/ClassResource|Speicherort|  
|DwpFiles/DwpFile|Speicherort|  
|FeatureManifests/FeatureManifest|Speicherort|  
|Ressourcen oder Ressourcengruppe|Speicherort|  
|"RootFiles" RootFile /|Speicherort|  
|SiteDefinitionManifests/SiteDefinitionManifest|Speicherort|  
|WebTempFile|Speicherort|  
|TemplateFiles/TemplateFile|Speicherort|  
|SolutionDependency|SolutionID|  
  
## <a name="manually-add-deployed-files"></a>Manuelles Hinzufügen von bereitgestellten Dateien
 Einige Elemente von Manifesten, z. B. ApplicationResourceFile und DwpFiles, geben Sie einen Speicherort, der einen Dateinamen enthält. Allerdings ist einen Eintrag für Datei hinzufügen, um die Manifestvorlage nicht die zugrunde liegende Datei für das Paket hinzufügen. Sie müssen die Datei hinzufügen, um das Projekt in das Paket einzuschließen, und legen Sie dessen Eigenschaft "Bereitstellungstyp" entsprechend fest.  
  
## <a name="see-also"></a>Siehe auch
 [Packen und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
