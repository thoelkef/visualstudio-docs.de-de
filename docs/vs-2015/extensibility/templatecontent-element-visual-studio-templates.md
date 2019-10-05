---
title: TemplateContent-Element (Visual Studio-Vorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#TemplateContent
helpviewer_keywords:
- TemplateContent element [Visual Studio project templates]
ms.assetid: 90ae401c-b294-49ac-98da-e0d274f5bebb
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: fe87bff62c1044442b579664fb789f918a2e6c2d
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "68186462"
---
# <a name="templatecontent-element-visual-studio-templates"></a>TemplateContent-Element (Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt den Inhalt der Vorlage.  
  
 \<VSTemplate>  
 \<TemplateContent >  
  
## <a name="syntax"></a>Syntax  
  
```  
<TemplateContent>  
    ...  
</TemplateContent>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|[BuildOnLoad](../extensibility/buildprojectonload-visual-studio-templates.md)|Gibt an, ob die Projektmappe zu erstellen, wenn ein Projekt aus der Vorlage erstellt wird.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, Dateien oder Verzeichnisse dem Projekt hinzu.|  
|[Verweise](../extensibility/references-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt an, die Verweise der Assembly, die für eine Item-Vorlage erforderlich sind.|  
|[ProjectItem](../extensibility/projectitem-element-visual-studio-item-templates.md)|Optionales Element.<br /><br /> Gibt eine Datei, die in der Vorlage enthalten sind.|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt alle benutzerdefinierten Parameter ab, die verwendet werden, wenn ein Projekt oder Element aus der Vorlage erstellt wird.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[VSTemplate](../extensibility/vstemplate-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Enthält alle Metadaten für die Projektvorlage, Item-Vorlage oder Starterkits.|  
  
## <a name="remarks"></a>Hinweise  
 `TemplateContent` ist ein erforderliches Element.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../includes/csprcs-md.md)]-Anwendung veranschaulicht.  
  
```  
<VSTemplate Type="Project" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>My template</Name>  
        <Description>A basic starter kit</Description>  
        <Icon>TemplateIcon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <Project File="MyStarterKit.csproj">  
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
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
