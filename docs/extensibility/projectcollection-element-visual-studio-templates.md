---
title: ProjectCollection-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectCollection
helpviewer_keywords:
- <ProjectCollection> element [Visual Studio Templates]
- ProjectCollection element [Visual Studio Templates]
ms.assetid: deb27180-2035-49ed-b835-c47bb3cd2f8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 12a22ca28c90ed1df69529ed3004b417b5e04276
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701980"
---
# <a name="projectcollection-element-visual-studio-templates"></a>ProjectCollection-Element (Visual Studio-Vorlagen)
Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.

 \<VSTemplate \<> TemplateContent> \<ProjectCollection>

## <a name="syntax"></a>Syntax

```xml
<ProjectCollection>
    <ProjectTemplateLink> ... </ProjectTemplateLink>
    <SolutionFolder> ... </SolutionFolder>
</ProjectCollection>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute
 Keine.

### <a name="child-elements"></a>Untergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectTemplateLink](../extensibility/projecttemplatelink-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gibt ein Projekt in einer Vorlage mit mehreren Projekten an.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Optionales Element.<br /><br /> Gruppiert Projekte in Vorlagen für mehrere Projekte.|

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Erforderliches Element<br /><br /> Gibt den Inhalt der Vorlage an.|

## <a name="remarks"></a>Bemerkungen
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Das `ProjectCollection` Element wird verwendet, um die Projekte anzugeben, die in der Vorlage enthalten werden sollen. Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter [Gewusst wie: Erstellen von Vorlagen für mehrere Projekte](../ide/how-to-create-multi-project-templates.md).

## <a name="example"></a>Beispiel
 Dieses Beispiel zeigt eine einfache *Stammdatei mit* mehreren Projekten . In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird. Wenn `ProjectName` das Attribut nicht vorhanden ist, wird der Name der *.vstemplate-Datei* als Projektname verwendet.

```
<VSTemplate Version="3.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Gewusst wie: Erstellen von Vorlagen für mehrere Projekte](../ide/how-to-create-multi-project-templates.md)
