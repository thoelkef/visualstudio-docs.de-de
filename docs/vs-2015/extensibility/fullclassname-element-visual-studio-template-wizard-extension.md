---
title: FullClassName-Element (Erweiterung für Visual Studio-Vorlagen-Assistenten) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#FullClassName
helpviewer_keywords:
- FullClassName element [Visual Studio project template]
ms.assetid: 651e1010-d529-4856-85ff-c77ceca5d2ed
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e7de1984a10d80e5136a9a01a1e1dae8ee5226f9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51796765"
---
# <a name="fullclassname-element-visual-studio-template-wizard-extension"></a>FullClassName-Element (Assistentenerweiterung für Visual Studio-Vorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Der vollqualifizierte Name der Klasse, die implementiert die `IWizard` Schnittstelle.  
  
 \<VSTemplate>  
 \<WizardExtension >  
 ...  
 \<FullClassName >  
  
## <a name="syntax"></a>Syntax  
  
```  
<FullClassName>ClassName</FullClassName>  
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
|[WizardExtension](../extensibility/wizardextension-element-visual-studio-templates.md)|Enthält die Registrierungselemente für die Anpassung von des Vorlagen-Assistenten.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Dieser Text gibt die Klasse, implementiert die `IWizard` Schnittstelle. Die angegebene Klasse muss vorhanden sein, in der Assembly, die gemäß der [Assembly](../extensibility/assembly-element-visual-studio-template-wizard-extension.md) Element.  
  
## <a name="remarks"></a>Hinweise  
 `FullClassName` ist ein erforderliches untergeordnetes Element von `WizardExtension`.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für die standard-Projektvorlage für eine [!INCLUDE[csprcs](../includes/csprcs-md.md)] Windows-Anwendung.  
  
```  
<VSTemplate Version="3.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyTemplate</Name>  
        <Description>Template using IWizard extension</Description>  
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
    <WizardExtension>  
        <Assembly>MyWizard, Version=1.0.3300.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a, Custom=null</Assembly>  
        <FullClassName>MyWizard.CustomWizard</FullClassName>  
    </WizardExtension>  
</VSTemplate>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Verwenden von Assistenten mit Projektvorlagen](../extensibility/how-to-use-wizards-with-project-templates.md)

