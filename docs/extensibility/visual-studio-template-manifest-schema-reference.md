---
title: Visual Studio-Vorlagenmanifest-Schemareferenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dbe46851d9df85569be796b4147217bd7db450ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697985"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Visual Studio-Vorlagenmanifestschemareferenz
Dieses Schema beschreibt das Format der Visual Studio-Vorlagenmanifestdateien (*.vstman*), die für Visual Studio-Projekt- oder Elementvorlagen generiert werden. Das Schema beschreibt auch den Speicherort und andere relevante Informationen zur Vorlage.

 : Da es separate Element- und Projektvorlagenverzeichnisse gibt, sollte ein Manifest niemals über eine Mischung aus Element- und Projektvorlagen verfügen.

> [!IMPORTANT]
> Dieses Manifest ist ab Visual Studio 2017 verfügbar.

## <a name="vstemplatemanifest-element"></a>VSTemplateManifest-Element
 Das Stammelement des Manifests.

### <a name="attributes"></a>Attribute

- **Version**: Eine Zeichenfolge, die die Version des Vorlagenmanifests darstellt. Erforderlich.

- **Gebietsschema**: Eine Zeichenfolge, die das Gebietsschema oder die Gebietsschemas des Vorlagenmanifests darstellt. Der Gebietsschemawert gilt für alle Vorlagen. Sie müssen für jedes Gebietsschema ein separates Manifest verwenden. Optional.

### <a name="child-elements"></a>Untergeordnete Elemente

- **VSTemplateContainer** Optional.

- **VSTemplateDir** Optional.

### <a name="parent-element"></a>Übergeordnetes Element
 Keine.

## <a name="vstemplatecontainer"></a>VSTemplateContainer
 Der Container der Vorlagenmanifestelemente. Ein Manifest verfügt über einen Vorlagencontainer für jede von ihm definierte Vorlage.

### <a name="attributes"></a>Attribute
 **VSTemplateType**: Ein Zeichenfolgenwert, der den`"Project"` `"Item"`Typ `"ProjectGroup"`der Vorlage angibt ( , , oder ). Erforderlich

### <a name="child-elements"></a>Untergeordnete Elemente

- **RelativePathOnDisk**: Der relative Pfad der Vorlagendatei auf dem Datenträger. Dieser Speicherort definiert auch die Platzierung der Vorlage in der Vorlagenstruktur, die im Dialogfeld **Neues Projekt** oder **Neues Element** angezeigt wird. Bei Vorlagen, die als Verzeichnis und einzelne Dateien bereitgestellt werden, bezieht sich dieser Pfad auf das Verzeichnis, das die Vorlagendateien enthält. Bei Vorlagen, die als *ZIP-Datei* bereitgestellt werden, sollte dieser Pfad der Pfad zur *ZIP-Datei* sein.

- **VSTemplateHeader: Ein [TemplateData-Element,](../extensibility/templatedata-element-visual-studio-templates.md) das den Header beschreibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **VSTemplateManifest**

## <a name="vstemplatedir"></a>VSTemplateDir
 Beschreibt das Verzeichnis, in dem sich die Vorlage befindet. Ein Manifest kann mehrere **VSTemplateDir-Einträge** enthalten, um lokalisierten Namen und Sortierreihenfolge für Verzeichnisse bereitzustellen, um deren Darstellung in der Vorlagenkategoriestruktur zu steuern.

 Aufgrund ihres Designs sollten **VSTemplateDir-Einträge** nur in nicht gebietsschema-angegebenen Manifesten angezeigt werden.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

- **RelativePath**: Der Pfad der Vorlage. Es kann nur einen Eintrag pro Pfad geben, so dass der erste für alle Manifeste gewinnt.

- **LocalizedName**: Ein **NameDescriptionIcon-Element,** das den lokalisierten Namen angibt. Optional.

- **SortOrder**: Eine Zeichenfolge, die die Sortierreihenfolge angibt. Optional.

- **ParentFolderOverrideName**: Der überschriebene Name des übergeordneten Ordners. Optional. Dieses Element **Name** verfügt über ein Name-Attribut, bei dem es sich um einen Zeichenfolgenwert handelt, der den Namen angibt.

### <a name="parent-element"></a>Übergeordnetes Element
 **VSTemplateManifest**

## <a name="namedescriptionicon"></a>NameDescriptionIcon
 Gibt den Namen und die Beschreibung an, möglicherweise für lokalisierte Vorlagen. Siehe **LocalizedName** oben.

### <a name="attributes"></a>Attribute

- **Paket**: Ein Zeichenfolgenwert, der das Paket angibt. Optional.

- **ID**: Ein Zeichenfolgenwert, der die ID angibt. Optional.

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-element"></a>Übergeordnetes Element
 **LocalizedName**

## <a name="examples"></a>Beispiele
 Der folgende Code ist ein Beispiel für eine Projektvorlage *.vstman-Datei.*

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

 Der folgende Code ist ein Beispiel für eine Item-Vorlage *.vstman-Datei.*

```xml
<VSTemplateManifest Version="1.0" Locale="1033" xmlns="http://schemas.microsoft.com/developer/vstemplatemanifest/2015">
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
