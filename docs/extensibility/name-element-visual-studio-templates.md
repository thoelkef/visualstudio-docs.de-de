---
title: Namen von Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#Name
helpviewer_keywords:
- Name element [Visual Studio project templates]
ms.assetid: 48788dbf-7da0-4443-8061-aab966fc22c8
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ca61a572ee923b5f9fa3f3999554d36057f4dd91
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53925484"
---
# <a name="name-element-visual-studio-templates"></a>Name-Element (Visual Studio-Vorlagen)
Gibt den Namen der Vorlage an, wie in der **neues Projekt** oder **neues Element hinzufügen** Dialogfeld.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<Name >  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<Name> Template Name </Name>  
```  
  
```xml  
<Name Package="{PackageID}" ID="ResourceID" />  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Package`|Optionales Attribut, für erweiterte Szenarien.<br /><br /> Eine GUID, der angibt, die Visual Studio-Paket-ID.|  
|`ID`|Optionales Attribut, für erweiterte Szenarien.<br /><br /> Gibt an, die Visual Studio-Ressourcen-ID.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie diese in den Dialogfeldern **Neues Projekt** oder **Neues Element hinzufügen** angezeigt wird.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich, es sei denn, die `Package` und `ID` Attribute verwendet werden.  
  
 Der Text gibt den Namen der Vorlage.  
  
## <a name="remarks"></a>Hinweise  
 `Name` ist ein erforderliches untergeordnetes Element von `TemplateData`.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.  
  
```xml  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyTemplate.csproj">  
            <ProjectItem>Form1.cs<ProjectItem>  
            <ProjectItem>Form1.Designer.cs</ProjectItem>  
            <ProjectItem>Program.cs</ProjectItem>  
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>  
            <ProjectItem>Properties\Resources.resx</ProjectItem>  
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>  
            <ProjectItem>Properties\Settings.settings</ProjectItem>  
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>  
        </Project>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlage](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)