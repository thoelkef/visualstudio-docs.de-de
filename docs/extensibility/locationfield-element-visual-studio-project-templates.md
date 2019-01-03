---
title: LocationField-Element (Visual Studio-Projektvorlagen) | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#LocationField
helpviewer_keywords:
- LocationField element [Visual Studio project templates]
ms.assetid: 6aaaa155-6ce0-4f7f-aa50-8d63d7a7c992
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1bbdff5e2dcee4611b5a46cc74f0255f94d30744
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53868496"
---
# <a name="locationfield-element-visual-studio-project-templates"></a>LocationField-Element (Visual Studio-Projektvorlagen)
Gibt an, ob die **Speicherort** Textfeld in die **neues Projekt** Dialogfeld ist aktiviert, deaktiviert oder ausgeblendet werden, für die Projektvorlage.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<LocationField >  
  
## <a name="syntax"></a>Syntax  
  
```  
<LocationField> Enabled/Disabled/Hidden </LocationField>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
 Keine  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Kategorisiert die Vorlage und definiert, wie es in einem angezeigt. die **neues Projekt**.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Gültigen Werte sind:  
  
-   `Enabled`, der angibt, dass die **Speicherort** im Feld der **neues Projekt** Dialogfeld ist aktiviert.  
  
-   `Disabled`, der angibt, dass die **Speicherort** im Feld der **neues Projekt** Dialogfeld deaktiviert ist.  
  
-   `Hidden`, der angibt, dass die **Speicherort** im Feld der **neues Projekt** Dialogfeld ausgeblendet wird.  
  
## <a name="remarks"></a>Hinweise  
 Der Standardwert ist `Enabled`.  
  
 Die **Speicherort** Textfeld in die **neues Projekt** Dialogfeld kann Benutzer das Standardverzeichnis ändern, in dem neue Projekte gespeichert werden.  
  
 Der Wert angegeben wird, der `Location` Element wird im Dialogfeld nur berücksichtigt, wenn das zugrunde liegende Projektsystem ihn unterstützt.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Vorlage veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic template</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <LocationField>Disabled</LocationField>  
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