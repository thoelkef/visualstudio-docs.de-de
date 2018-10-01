---
title: Visual Studio-Vorlage Manifest Schemareferenz | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 4
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b079e6b7356cdd84a98314beef95f4b1a8fbc5ee
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47511668"
---
# <a name="visual-studio-template-manifest-schema-reference"></a>Schemareferenz zum Visual Studio-Vorlagenmanifest
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Visual Studio-Manifest Schemareferenz zu Vorlagen](https://docs.microsoft.com/visualstudio/extensibility/visual-studio-template-manifest-schema-reference).  
  
Dieses Schema beschreibt das Format für die Visual Studio-Manifest (vstman) Vorlagendateien für Visual Studio Projekt- oder Elementvorlagen generiert und beschreibt den Speicherort und andere relevante Informationen zur Vorlage.  
  
 : Da es sich um eine separate Element und den Projektverzeichnissen-Vorlage vorhanden sind, müssen ein Manifest noch nie eine Kombination von Element- und Projektvorlagen.  
  
> [!IMPORTANT]
>  Dieses Manifest ist verfügbar in Visual Studio "15" Preview 2.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest-Element  
 Das Stammelement des Manifests.  
  
### <a name="attributes"></a>Attribute  
  
-   **Version**: eine Zeichenfolge, die die Version des Manifests Vorlage darstellt. Erforderlich.  
  
-   **Gebietsschema**: eine Zeichenfolge, die dem Gebietsschema oder Gebietsschemas des Manifests Vorlage darstellt. Die Gebietsschemawert gilt für alle Vorlagen, müssen Sie ein eigenes Manifest für jedes Gebietsschema verwenden. Dies ist optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **VSTemplateContainer** Optional.  
  
-   **VSTemplateDir** Optional.  
  
### <a name="parent-element"></a>Parent-Element  
 Keine  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Der Container der Vorlage manifest Elemente. Ein Manifest verfügt über eine Vorlagencontainers für jede Vorlage, die sie definiert.  
  
### <a name="attributes"></a>Attribute  
 **VSTemplateType** : ein Zeichenfolgenwert, der angibt, den Typ der Vorlage (`"Project"`, `"Item"`, oder `"ProjectGroup"`). Erforderlich  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePathOnDisk**: der relative Pfad der Vorlagendatei auf dem Datenträger. Hier definiert die Platzierung der Vorlage auch in der Struktur der Vorlage angezeigt, der **neues Projekt** oder **neues Element** Dialogfeld. Für Vorlagen, die als ein Verzeichnis und die einzelnen Dateien bereitgestellt werden bezieht sich dieser Pfad zu dem Verzeichnis, das die Vorlagendateien enthält. Für Vorlagen, die als ZIP-Datei bereitgestellt werden sollten diesen Pfad, den Pfad zur ZIP-Datei sein.  
  
-   **VSTemplateHeader** : ein [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element, das den Header beschreibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Beschreibt das Verzeichnis, in dem die Vorlage befindet. Ein Manifest kann mehrere enthalten **VSTemplateDir** Einträgen zum Bereitstellen von lokalisierten und die Sortierreihenfolge für Verzeichnisse Reihenfolge ihrer Darstellung in der Struktur der Vorlage Kategorie-steuern.  
  
 Aufgrund ihrer Konstruktion **VSTemplateDir** Einträge sollten nur in der angegebenen Manifeste nicht um ein Gebietsschema angezeigt werden.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePath**: der Pfad der Vorlage. Es können nur einen Eintrag pro Pfad vorhanden sein, damit die erste Bedingung für alle Manifeste gewinnen wird.  
  
-   **LocalizedName**: ein **NameDescriptionIcon** Element, das den lokalisierten Namen angibt. Dies ist optional.  
  
-   **SortOrder** : eine Zeichenfolge, die Sortierreihenfolge angibt. Dies ist optional.  
  
-   **ParentFolderOverrideName**: den außer Kraft gesetzten Namen des übergeordneten Ordners. Dies ist optional. Dieses Element verfügt über eine **Namen** Attribut, das einen Zeichenfolgenwert, der den Namen angibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Gibt den Namen und Beschreibung, die möglicherweise für lokalisierte Vorlagen. Finden Sie unter **LocalizedName** oben.  
  
### <a name="attributes"></a>Attribute  
  
-   **Paket**: ein Zeichenfolgenwert, der angibt, das Paket. Dies ist optional.  
  
-   **ID**: ein Zeichenfolgenwert, der angibt, die-ID. Dies ist optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-element"></a>Parent-Element  
 **LocalizedName**  
  
## <a name="examples"></a>Beispiele  
 Folgendes ist ein Beispiel für eine Vorlage vstman-Projektdatei.  
  
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
  
 Folgendes ist ein Beispiel für ein Element Vorlage vstman-Datei.  
  
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

