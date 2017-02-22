---
title: "Common MSBuild Project Items | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, common project items"
ms.assetid: 1eba3721-cc12-4b80-9987-84923ede5e2e
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Common MSBuild Project Items
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] ist ein Element ein benannter Verweis auf eine oder mehrere Dateien.  Elemente enthalten Metadaten wie Dateinamen, Pfade und Versionsnummern.  Alle Projekttypen in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] haben mehrere Elemente gemeinsam.  Diese Elemente werden in der Datei microsoft.build.commontypes.xsd definiert.  
  
## Gemeinsame Elemente  
 In der folgenden Liste werden alle gemeinsamen Projektelemente aufgeführt.  
  
### Verweis  
 Stellt einen Assemblyverweis \(verwaltet\) im Projekt dar.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|HintPath|Optionale Zeichenfolge.  Relativer oder absoluter Pfad der Assembly.|  
|Name|Optionale Zeichenfolge.  Der Anzeigename der Assembly, z. B. "System.Windows.Forms".|  
|FusionName|Optionale Zeichenfolge.  Gibt den einfachen oder starken Fusionsnamen für das Element an.<br /><br /> Wenn dieses Attribut vorhanden ist, führt dies zu Zeiteinsparungen, da die Assemblydatei zum Abrufen des Fusionsnamens nicht geöffnet werden muss.|  
|SpecificVersion|Optionaler boolescher Wert.  Gibt an, ob nur auf die Version im Fusionsnamen verwiesen werden soll.|  
|Aliase|Optionale Zeichenfolge.  Alle Aliase für den Verweis.|  
|Privat|Optionaler boolescher Wert.  Gibt an, ob der Verweis in den Ausgabeordner kopiert werden soll.  Dieses Attribut entspricht der Eigenschaft **Lokale Kopie** des Verweises in der Visual Studio\-IDE.|  
  
### COMReference  
 Stellt einen COM\-Komponentenverweis \(nicht verwaltet\) im Projekt dar.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|Name|Optionale Zeichenfolge.  Der Anzeigename der Komponente.|  
|Guid|Optionale Zeichenfolge.  Eine GUID für die Komponente im Format {12345678\-1234\-1234\-1234\-1234567891234}.|  
|VersionMajor|Optionale Zeichenfolge.  Der Hauptteil der Versionsnummer der Komponente.  Beispielsweise "5", wenn die Versionsnummer "5.46" lautet.|  
|VersionMinor|Optionale Zeichenfolge.  Der zweite Teil der Versionsnummer \(Nebenversionsnummer\) der Komponente.  Beispielsweise "46", wenn die Versionsnummer "5.46" lautet.|  
|LCID|Optionale Zeichenfolge.  Die LocaleID \(Gebietsschema\-ID\) für die Komponente.|  
|WrapperTool|Optionale Zeichenfolge.  Der Name des Wrappertools, das auf die Komponente angewendet wird, z. B. "tlbimp".|  
|Isolated|Optionaler boolescher Wert.  Gibt an, ob die Komponente eine registrierungsfreie Komponente ist.|  
  
### COMFileReference  
 Stellt eine Liste von Typbibliotheken dar, die an das ResolvedComreference\-Ziel übertragen werden.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|WrapperTool|Optionale Zeichenfolge.  Der Name des Wrappertools, das auf die Komponente angewendet wird, z. B. "tlbimp".|  
  
### NativeReference  
 Stellt eine systemeigene Manifestdatei oder einen Verweis auf eine solche Datei dar.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|Name|Erforderliche Zeichenfolge.  Der Basisname der Manifestdatei.|  
|HintPath|Erforderliche Zeichenfolge.  Der relative Pfad der Manifestdatei.|  
  
### ProjectReference  
 Stellt einen Verweis auf ein anderes Projekt dar.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|Name|Optionale Zeichenfolge.  Der Anzeigename des Verweises.|  
|Project|Optionale Zeichenfolge.  Eine GUID für den Verweis im Format {12345678\-1234\-1234\-1234\-1234567891234}.|  
|Package|Optionale Zeichenfolge.  Der Pfad der Projektdatei, auf die verwiesen wird.|  
  
### Compile  
 Stellt die Quelldateien für den Compiler dar.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|DependentUpon|Optionale Zeichenfolge.  Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren.|  
|AutoGen|Optionaler boolescher Wert.  Gibt an, ob die Datei für das Projekt von der integrierten [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]\-Entwicklungsumgebung \(IDE\) generiert wurde.|  
|Link|Optionale Zeichenfolge.  Der anzuzeigende Notationspfad, wenn sich die Datei physisch außerhalb des Einflusses der Projektdatei befindet.|  
|Visible|Optionaler boolescher Wert.  Gibt an, ob die Datei im **Projektmappen\-Explorer** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.|  
|CopyToOutputDirectory|Optionale Zeichenfolge.  Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll.  Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest|  
  
### EmbeddedResource  
 Stellt Ressourcen dar, die in die generierte Assembly eingebettet werden.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|DependentUpon|Optionale Zeichenfolge.  Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren.|  
|Generator|Erforderliche Zeichenfolge.  Der Name eines die oft ausgegebene Befehlszeilen  Datei\-Generators, der über diesem Element ausgeführt wird.|  
|LastGenOutput|Erforderliche Zeichenfolge.  Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei\-Generator erstellt wurde, der über diesem Element ausgeführt wurde.|  
|CustomToolNamespace|Erforderliche Zeichenfolge.  Der Namespace, in dem ein beliebiger Datei\-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte.|  
|Link|Optionale Zeichenfolge.  Der Notationspfad wird angezeigt, wenn sich die Datei physisch außerhalb des Einflusses des Projekts befindet.|  
|Visible|Optionaler boolescher Wert.  Gibt an, ob die Datei im **Projektmappen\-Explorer** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.|  
|CopyToOutputDirectory|Optionale Zeichenfolge.  Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll.  Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest|  
|LogicalName|Erforderliche Zeichenfolge.  Der logische Name der eingebetteten Ressource.|  
  
### Inhalt  
 Stellt Dateien dar, die zwar nicht in das Projekt kompiliert werden, jedoch möglicherweise mit dem Projekt eingebettet oder veröffentlicht werden.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|DependentUpon|Optionale Zeichenfolge.  Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren.|  
|Generator|Erforderliche Zeichenfolge.  Der Name eines die oft ausgegebene Befehlszeilen  Datei\-Generators, der über diesem Element ausgeführt wird.|  
|LastGenOutput|Erforderliche Zeichenfolge.  Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei\-Generator erstellt wurde, der über diesem Element ausgeführt wurde.|  
|CustomToolNamespace|Erforderliche Zeichenfolge.  Der Namespace, in dem ein beliebiger Datei\-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte.|  
|Link|Optionaler boolescher Wert.  Gibt an, ob die Datei im **Projektmappen\-Explorer** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.|  
|PublishState|Erforderliche Zeichenfolge.  Der Inhalt kann einen der folgenden Veröffentlichungszustände aufweisen:<br /><br /> -   Standard<br />-   Included<br />-   Excluded<br />-   DataFile<br />-   Vorbereitungsmaßnahme|  
|IsAssembly|Optionaler boolescher Wert.  Gibt an, ob die Datei eine Assembly ist.|  
|Visible|Optionaler boolescher Wert.  Gibt an, ob die Datei im **Projektmappen\-Explorer** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.|  
|CopyToOutputDirectory|Optionale Zeichenfolge.  Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll.  Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest|  
  
### Keine  
 Stellt Dateien dar, die keine Rolle im Buildprozess haben sollen.  
  
|Elementname|Beschreibung|  
|-----------------|------------------|  
|DependentUpon|Optionale Zeichenfolge.  Gibt die Datei an, von der diese Datei abhängt, um ordnungsgemäß zu kompilieren.|  
|Generator|Erforderliche Zeichenfolge.  Der Name eines die oft ausgegebene Befehlszeilen  Datei\-Generators, der über diesem Element ausgeführt wird.|  
|LastGenOutput|Erforderliche Zeichenfolge.  Der Name der Datei, die von einem die oft ausgegebene Befehlszeilen  Datei\-Generator erstellt wurde, der über diesem Element ausgeführt wurde.|  
|CustomToolNamespace|Erforderliche Zeichenfolge.  Der Namespace, in dem ein beliebiger Datei\-Generator, der über diesem Element ausgeführt wird, Code erstellen sollte.|  
|Link|Optionale Zeichenfolge.  Der anzuzeigende Notationspfad, wenn sich die Datei physisch außerhalb des Einflusses des Projekts befindet.|  
|Visible|Optionaler boolescher Wert.  Gibt an, ob die Datei im **Projektmappen\-Explorer** in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] angezeigt wird.|  
|CopyToOutputDirectory|Optionale Zeichenfolge.  Bestimmt, ob die Datei in das Ausgabeverzeichnis kopiert werden soll.  Gültige Werte:<br /><br /> 1.  Nie<br />2.  Always<br />3.  PreserveNewest|  
  
### BaseApplicationManifest  
 Stellt das Basisanwendungsmanifest für den Build dar und enthält Sicherheitsinformationen für die [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)]\-Bereitstellung.  
  
### CodeAnalysisImport  
 Stellt das zu importierende FxCop\-Projekt dar.  
  
### Importieren  
 Stellt Assemblys dar, deren Namespaces vom [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler importiert werden sollen.  
  
## Siehe auch  
 [Common MSBuild Project Properties](../msbuild/common-msbuild-project-properties.md)