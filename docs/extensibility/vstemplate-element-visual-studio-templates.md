---
title: VSTemplate-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: http://schemas.microsoft.com/developer/vstemplate/2005#VSTemplate
helpviewer_keywords: VSTemplate element [Visual Studio project templates]
ms.assetid: f8ac561b-3b0b-4246-9ec9-118d2447e9a9
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 1c9fe87ae48c705e447b4fc5bd2834a417c4e8d4
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vstemplate-element-visual-studio-templates"></a>VSTemplate-Element (Visual Studio-Vorlagen)
Enthält alle Metadaten für die Projektvorlage, Elementvorlage oder Starterkit.  
  
## <a name="syntax"></a>Syntax  
  
```  
<VSTemplate Type="TemplateType" Version="x.x.x">  
    <TemplateData>    </TemplateData>  
    <TemplateContent>    </TemplateContent>  
    ...  
</VSTemplate>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Type`|Identifiziert die Vorlage als eine Projektvorlage oder eine Elementvorlage. Dieses Attribut kann den Wert des haben `Project` oder `Item`.|  
|`Version`|Gibt eine Versionsnummer für die Vorlage an. Vorlagen in [!INCLUDE[vs_dev10_long](../code-quality/includes/vs_dev10_long_md.md)] und [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] haben eine `Version` -Attributwert `3.0.0`.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt an, die kategorisiert die Vorlage und definiert, wie er im angezeigt der **neues Projekt** oder **neues Element hinzufügen** (Dialogfeld).|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element.<br /><br /> Gibt den Inhalt der Vorlage.|  
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Optionales Element.|  
|[WizardData](../extensibility/wizarddata-element-visual-studio-templates.md)|Optionales Element.|  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
 Keine  
  
## <a name="remarks"></a>Hinweise  
 Die `VSTemplate` Element ist das Stammelement der VSTEMPLATE-Dateien.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]-Anwendung veranschaulicht.  
  
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
            <ProjectItem>Form1.cs</ProjectItem>  
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