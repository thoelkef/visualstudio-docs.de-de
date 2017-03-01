---
title: Visual Studio-Vorlage Manifest Schemareferenz | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bc7d0a81-0df5-41a9-a912-1b30e5da1d13
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 0f4abf286dc8b1cf00e47468ddaa4831747a059d
ms.lasthandoff: 02/22/2017

---
# <a name="visual-studio-template-manifest-schema-reference"></a>Referenz zu Visual Studio-Vorlage Manifestschema
Dieses Schema beschreibt das Format der Visual Studio-Manifest (.vstman) Vorlagendateien für Visual Studio-Projekt oder Element-Vorlagen generiert und den Speicherort und andere relevante Informationen über die Vorlage beschreibt.  
  
 : Da separate Element und Projektverzeichnisse Vorlage verfügbar sind, sollte ein Manifest nie eine Kombination von Element- und Projektvorlagen enthalten.  
  
> [!IMPORTANT]
>  Dieses Manifest ist verfügbar in Visual Studio 2017 ab.  
  
## <a name="vstemplatemanifest-element"></a>VSTemplateManifest-Element  
 Das Stammelement des Manifests.  
  
### <a name="attributes"></a>Attribute  
  
-   **Version**: eine Zeichenfolge, die die Version des Manifests Vorlage darstellt. Erforderlich.  
  
-   **Gebietsschema**: eine Zeichenfolge, die das Gebietsschema oder Gebietsschemas des Manifests Vorlage darstellt. Gebietsschemawert gilt für alle Vorlagen, daher müssen Sie ein eigenes Manifest für jedes Gebietsschema verwenden. Optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **VSTemplateContainer** Optional.  
  
-   **VSTemplateDir** Optional.  
  
### <a name="parent-element"></a>Parent-Element  
 Keine  
  
## <a name="vstemplatecontainer"></a>VSTemplateContainer  
 Der Container der Vorlage manifest Elemente. Ein Manifest besitzt eine Vorlagencontainers für jede Vorlage, die sie definiert.  
  
### <a name="attributes"></a>Attribute  
 **VSTemplateType** : ein String-Wert, der den Typ der Vorlage angibt (`"Project"`, `"Item"`, oder `"ProjectGroup"`). Erforderlich  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePathOnDisk**: der relative Pfad der Vorlagendatei auf dem Datenträger. Dieser Speicherort definiert auch die Platzierung der Vorlage in der Struktur der Vorlage angezeigt, der **neues Projekt** oder **neues Element** Dialogfeld. Für Vorlagen, die als ein Verzeichnis und die einzelnen Dateien bereitgestellt werden bezieht sich dieser Pfad zum Verzeichnis mit die Vorlagendateien. Für Vorlagen, die als ZIP-Datei bereitgestellt werden sollte dieser Pfad den Pfad zu der ZIP-Datei.  
  
-   **VSTemplateHeader** : ein [TemplateData](../extensibility/templatedata-element-visual-studio-templates.md) Element, das den Header beschreibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="vstemplatedir"></a>VSTemplateDir  
 Beschreibt das Verzeichnis, in dem die Vorlage befindet. Ein Manifest kann mehrere enthalten **VSTemplateDir** Einträge lokalisierten Namen und Sortierreihenfolge für Verzeichnisse ihre Darstellung in der Struktur der Vorlage Kategorie angeben.  
  
 Aufgrund ihrer Konstruktion **VSTemplateDir** Einträge sollten nur in nicht um ein Gebietsschema angegebenen Manifeste angezeigt werden.  
  
### <a name="attributes"></a>Attribute  
 Keine.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
-   **RelativePath**: der Pfad der Vorlage. Daher zuerst für alle Manifeste gewinnen kann nur einen Eintrag pro Pfad sein.  
  
-   **LocalizedName**: ein **NameDescriptionIcon** Element, das den lokalisierten Namen angibt. Optional.  
  
-   **SortOrder** : eine Zeichenfolge, die die Sortierreihenfolge angibt. Optional.  
  
-   **ParentFolderOverrideName**: der überschriebenen Name des übergeordneten Ordners. Optional. Dieses Element verfügt über eine **Namen** Attribut, das einen Zeichenfolgenwert, der den Namen angibt.  
  
### <a name="parent-element"></a>Parent-Element  
 **VSTemplateManifest**  
  
## <a name="namedescriptionicon"></a>NameDescriptionIcon  
 Gibt den Namen und die Beschreibung möglicherweise für lokalisierte Vorlagen. Finden Sie unter **LocalizedName** oben.  
  
### <a name="attributes"></a>Attribute  
  
-   **Paket**: ein String-Wert, der das Paket angibt. Optional.  
  
-   **ID**: ein String-Wert, der angibt, die-ID. Optional.  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-element"></a>Parent-Element  
 **LocalizedName**  
  
## <a name="examples"></a>Beispiele  
 Im folgenden ist ein Beispiel für eine Vorlage .vstman-Projektdatei.  
  
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
  
 Im folgenden ist ein Beispiel für eine Vorlagendatei .vstman eines Elements.  
  
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
