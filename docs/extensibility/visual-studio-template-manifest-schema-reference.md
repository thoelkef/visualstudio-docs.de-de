---
title: Visual Studio-Vorlage Manifest Schemareferenz | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: "3"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 87f676ef30da7c667c4ce2b688520a49ed1931c3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Manifest Visual Studio-Schemareferenz
Dieses Schema beschreibt das Format von der Visual Studio-Manifest (.vstman) Vorlagendateien für Visual Studio Projekt- oder Elementvorlagen generiert und beschreibt den Speicherort und andere relevante Informationen über die Vorlage.  
  
 : Da separates Element und Vorlage Projektverzeichnisse vorhanden sind, sollte ein Manifest nie eine Mischung aus Vorlagen für Element und Projekt haben.  
  
> [!IMPORTANT]
>  Dieses Manifest steht in Visual Studio 2017 ab.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest-Element  
 Das Stammelement des Manifests.  
  
### <a name="attributes"></a>Attribute  
  
-   **Version**: eine Zeichenfolge, die die Version des Manifests Vorlage darstellt. Erforderlich.  
  
-   **Gebietsschema**: eine Zeichenfolge, die das Gebietsschema oder die Gebietsschemas des Manifests Vorlage darstellt. Die Gebietsschemawert gilt für alle Vorlagen, müssen Sie ein separates Manifest für jedes Gebietsschema verwenden. Dies ist optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **VSTemplateContainer** Optional.  
  
-   **VSTemplateDir** Optional.  
  
### <a name="parent-element"></a>Parent-Element  
 Keine  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Der Container der Vorlage manifest Elemente. Ein Manifest ist eine Vorlage Container für jede Vorlage, die sie definiert.  
  
### <a name="attributes"></a>Attribute  
 **VSTemplateType** : ein Zeichenfolgenwert, der den Typ der Vorlage angibt (`"Project"`, `"Item"`, oder `"ProjectGroup"`). Erforderlich  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePathOnDisk**: der relative Pfad der Vorlagendatei auf dem Datenträger. Hier definiert die Platzierung der Vorlage auch in der Struktur der Vorlage angezeigt, der **neues Projekt** oder **neues Element** Dialogfeld. Für Vorlagen, die als ein Verzeichnis und einzelne Dateien bereitgestellt werden bezieht sich dieser Pfad zum Verzeichnis mit der Dateien. Für Vorlagen, die als ZIP-Datei bereitgestellt werden sollten diesen Pfad den Pfad zur ZIP-Datei sein.  
  
-   **VSTemplateHeader** : ein [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element, das den Header beschreibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Beschreibt das Verzeichnis, in dem die Vorlage befindet. Ein Manifest kann mehrere enthalten **VSTemplateDir** Einträge zum Bereitstellen von lokalisierten und die Sortierreihenfolge für Verzeichnisse Reihenfolge ihrer Darstellung in der Vorlage Kategoriestruktur steuern.  
  
 Aufgrund ihrer Konstruktion **VSTemplateDir** Einträge sollte nur in nicht-Gebietsschema angegebenen Manifeste angezeigt werden.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePath**: der Pfad der Vorlage. Damit die erste Vorlage für alle Manifeste gewinnen kann nur ein Eintrag pro Pfad sein.  
  
-   **LocalizedName**: ein **NameDescriptionIcon** Element, das den lokalisierten Namen angibt. Dies ist optional.  
  
-   **SortOrder** : eine Zeichenfolge, die Sortierreihenfolge angibt. Dies ist optional.  
  
-   **ParentFolderOverrideName**: den außer Kraft gesetzten Namen des übergeordneten Ordners. Dies ist optional. Dieses Element verfügt über eine **Namen** -Attribut, das ist ein Zeichenfolgenwert, der den Namen angibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Gibt den Name und Beschreibung, die möglicherweise für lokalisierte Vorlagen. Finden Sie unter **LocalizedName** oben.  
  
### <a name="attributes"></a>Attribute  
  
-   **Paket**: ein Zeichenfolgenwert, der das Paket angibt. Dies ist optional.  
  
-   **ID**: ein Zeichenfolgenwert, der angibt, die-ID. Dies ist optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-element"></a>Parent-Element  
 **LocalizedName**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden ist ein Beispiel einer Vorlage .vstman-Projektdatei.  
  
```xml  
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Project">  
    <RelativePathOnDisk>CSharp\1033\TestProjectTemplate</RelativePathOnDisk>  
    <TemplateFileName>TestProjectTemplate.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>TestProjectTemplate</Name>  
        <Description>TestProjectTemplate</Description>  
        <Icon>TestProjectTemplate.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <SortOrder>1000</SortOrder>  
        <TemplateID>aac0aeea-7883-4003-992f-937d53d70ab1</TemplateID>  
        <CreateNewFolder>true</CreateNewFolder>  
        <DefaultName>TestProjectTemplate</DefaultName>  
        <ProvideDefaultName>true</ProvideDefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```  
  
 Im folgenden ist ein Beispiel für ein Element .vstman Vorlagendatei.  
  
```  
VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">  
  <VSTemplateContainer TemplateType="Item">  
    <RelativePathOnDisk>CSharp\1033\ItemTemplate1</RelativePathOnDisk>  
    <TemplateFileName>ItemTemplate1.vstemplate</TemplateFileName>  
    <VSTemplateHeader>  
      <TemplateData xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <Name>ItemTemplate1</Name>  
        <Description>ItemTemplate1</Description>  
        <Icon>ItemTemplate1.ico</Icon>  
        <TemplateID>bfeadf8e-a251-4109-b605-516b88e38c8d</TemplateID>  
        <ProjectType>CSharp</ProjectType>  
        <RequiredFrameworkVersion>2.0</RequiredFrameworkVersion>  
        <NumberOfParentCategoriesToRollUp>1</NumberOfParentCategoriesToRollUp>  
        <DefaultName>Class.cs</DefaultName>  
      </TemplateData>  
    </VSTemplateHeader>  
  </VSTemplateContainer>  
</VSTemplateManifest>  
  
```