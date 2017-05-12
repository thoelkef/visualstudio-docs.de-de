---
title: "Zusammenf&#252;hren von XML in Funktions- und Paketmanifesten"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint-Entwicklung in Visual Studio, Packen"
ms.assetid: fc1cbd2a-0166-4f2f-a81b-4dac2fa7b0f3
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 9
---
# Zusammenf&#252;hren von XML in Funktions- und Paketmanifesten
  Funktionen und Pakete werden mithilfe von [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Manifestdateien definiert.  Bei diesen gepackten Manifesten handelt es sich um eine Kombination aus von Designern generierten Daten und benutzerdefiniertem [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Code, der von den Benutzern in die Manifestvorlage eingegeben wurde.  Beim Packen werden die benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Anweisungen durch [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] mit dem [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Code der Designer zur [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Manifestdatei zusammengeführt.  Ähnliche Elemente werden – mit Ausnahme der weiter unten angegebenen Zusammenführungsausnahmen – zusammengeführt, um [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Validierungsfehler nach dem Bereitstellen in SharePoint zu vermeiden sowie um kleinere und effizientere Manifestdateien zu erhalten.  
  
## Ändern der Manifeste  
 Zum direkten Ändern der gepackten Manifestdateien muss zunächst der Funktions\- oder der Paket\-Designer deaktiviert werden.  Sie können der Manifestvorlage jedoch manuell benutzerdefinierte [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Elemente hinzufügen. Verwenden Sie hierzu entweder den Funktions\- oder Paket\-Designer oder den [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Editor.  Weitere Informationen finden Sie unter [Gewusst wie: Anpassen einer SharePoint-Funktion](../sharepoint/how-to-customize-a-sharepoint-feature.md) und [Gewusst wie: Anpassen eines SharePoint-Lösungspakets](../sharepoint/how-to-customize-a-sharepoint-solution-package.md).  
  
## Zusammenführungsprozess für Funktions\- und Paketmanifeste  
 Wenn Sie benutzerdefinierte Elemente mit von Designern bereitgestellten Elementen kombinieren, wird von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] der folgende Prozess verwendet.  Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] wird überprüft, ob jedes Element einen eindeutigen Schlüsselwert besitzt.  Wenn ein Element über keinen eindeutigen Schlüsselwert verfügt, wird es an die gepackte Manifestdatei angefügt.  Auch Elemente, die mehrere, Schlüsseln können nicht zusammengeführt werden.  Deshalb werden sie an die Manifestdatei angefügt.  
  
 Besitzt ein Element einen eindeutigen Schlüssel, werden von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] die Werte des Designers und des benutzerdefinierten Schlüssels verglichen.  Stimmen die Werte überein, werden sie zu einem einzelnen Wert zusammengeführt.  Wenn sich die Werte unterscheiden, wird der Designerschlüsselwert verworfen, und der benutzerdefinierte Schlüsselwert wird verwendet.  Auch Auflistungen werden zusammengeführt.  Beispiel: Ist sowohl im vom Designer generierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Code als auch im benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Code eine Assemblies\-Auflistung vorhanden, enthält das gepackte Manifest lediglich eine einzelne Assemblies\-Auflistung.  
  
## Zusammenführungsausnahmen  
 Von [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] werden die meisten Designer\-[!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Elemente mit ähnlichen benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Elementen zusammengeführt. Voraussetzung ist allerdings, dass sie ein einzelnes, eindeutiges Attribut besitzen.  Einigen Elementen fehlt jedoch der erforderliche eindeutige Bezeichner für die [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Zusammenführung.  Diese Elemente werden als *Zusammenführungsausnahmen* bezeichnet.  In diesen Fällen werden die benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Elemente durch [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] nicht mit den von den Designern bereitgestellten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Elementen zusammengeführt, sondern stattdessen an die gepackte Manifestdatei angefügt.  
  
 Im Anschluss finden Sie eine Liste mit Zusammenführungsausnahmen für [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Manifestdateien für Funktionen und Pakete:  
  
|\-Designer|XML\-Element|  
|----------------|------------------|  
|Funktions\-Designer|ActivationDependency|  
|Funktions\-Designer|UpgradeAction|  
|Paket\-Designer|SafeControl|  
|Paket\-Designer|CodeAccessSecurity|  
  
## Funktionsmanifestelemente  
 Bei der folgenden Tabelle handelt es sich um eine Liste mit allen zusammenführbaren Funktionsmanifestelementen und den jeweils eindeutigen Schlüsseln für den Abgleich.  
  
|Elementname|Eindeutiger Schlüssel|  
|-----------------|---------------------------|  
|Feature \(alle Attribute\)|*Attribute Name* \(Jeder Attributname des Feature\-Elements ist ein eindeutiger Schlüssel.\)|  
|ElementFile|Speicherort|  
|ElementManifests\/ElementManifest|Speicherort|  
|Properties\/Property|Key|  
|CustomUpgradeAction|Name|  
|CustomUpgradeActionParameter|Name|  
  
> [!NOTE]  
>  Da das CustomUpgradeAction\-Element einzig im benutzerdefinierten [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]\-Editor geändert werden kann, hat der Verzicht auf eine Zusammenführung nur geringfügige Auswirkungen.  
  
## Paketmanifestelemente  
 Bei der folgenden Tabelle handelt es sich um eine Liste mit allen zusammenführbaren Paketmanifestelementen und den jeweils eindeutigen Schlüsseln für den Abgleich.  
  
|Elementname|Eindeutiger Schlüssel|  
|-----------------|---------------------------|  
|Solution \(alle Attribute\)|*Attribute Name* \(Jeder Attributname des Solution\-Elements ist ein eindeutiger Schlüssel.\)|  
|ApplicationResourceFiles\/ApplicationResourceFile|Speicherort|  
|Assemblies\/Assembly|Speicherort|  
|ClassResources\/ClassResource|Speicherort|  
|DwpFiles\/DwpFile|Speicherort|  
|FeatureManifests\/FeatureManifest|Speicherort|  
|Resources\/Resource|Speicherort|  
|RootFiles\/RootFile|Speicherort|  
|SiteDefinitionManifests\/SiteDefinitionManifest|Speicherort|  
|WebTempFile|Speicherort|  
|TemplateFiles\/TemplateFile|Speicherort|  
|SolutionDependency|SolutionID|  
  
## Manuelles Hinzufügen bereitgestellter Dateien  
 Von einigen Manifestelementen \(beispielsweise "ApplicationResourceFile" und "DwpFiles"\) wird ein Speicherort mit einem Dateinamen angegeben.  Durch Hinzufügen eines Dateinameneintrags zur Manifestvorlage wird die zugrunde liegende Datei jedoch nicht dem Paket hinzugefügt.  Die Datei muss dem Projekt hinzugefügt werden, um sie in das Paket einzuschließen und die Eigenschaft "Bereitstellungstyp" entsprechend festzulegen.  
  
## Siehe auch  
 [Verpacken und Bereitstellen von SharePoint-Lösungen](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)   
 [Erstellen und Debuggen von SharePoint-Lösungen](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  