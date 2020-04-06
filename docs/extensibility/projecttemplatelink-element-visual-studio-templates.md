---
title: ProjectTemplateLink-Element (Visual Studio-Vorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectTemplateLink
helpviewer_keywords:
- <ProjectTemplateLink> element [Visual Studio Templates]
- ProjectTemplateLink element [Visual Studio Templates]
ms.assetid: b0449111-8b48-45a1-a031-ea24b765e969
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6d402b6605f2e01a20d400c2c33573c686a1cdd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701822"
---
# <a name="projecttemplatelink-element-visual-studio-templates"></a>ProjectTemplateLink-Element (Visual Studio-Vorlagen)
Gibt den Pfad zur *.vstemplate-Datei* eines Projekts in einer Vorlage mit mehreren Projekten an.

 \<VSTemplate \<> \<TemplateContent> \<ProjectCollection> ProjectTemplateLink> \<-or- VSTemplate> \<TemplateContent> \<ProjectCollection> \<Projektmappe> \<ProjectTemplateLink>

## <a name="syntax"></a>Syntax

```xml
<ProjectTemplateLink ProjectName="Name">
    PathToTemplateFile
</ProjectTemplateLink>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

|attribute|BESCHREIBUNG|
|---------------|-----------------|
|`ProjectName`|Optionales Attribut.<br /><br /> Gibt in einer Vorlage für mehrere Projekte den Namen für jedes einzelne Projekt an. Das Dialogfeld **Neues Projekt** kann einzelnen Projekten keine Namen zuweisen.|
|`CopyParameters`|Ermöglicht, dass alle Variablen in der Hauptgruppenvorlage in jede der verknüpften Vorlagen kopiert werden können.<br /><br /> Die Parameter in verknüpften Vorlagen enthalten ein Präfix `"$ext_*$"`. Wenn der `$projectname$` Parameter in der übergeordneten Gruppenvorlage beispielsweise den Wert **ExampleProject1**hat, wenn die verknüpfte `$ext_projectname$`Vorlage an der `$projectname$` Reihe ist, erhält sie einen Parameter , der eine Kopie des Parameters aus der übergeordneten Gruppenvorlage ist.<br /><br /> Dadurch können verknüpfte Vorlagen einige häufig verwendete Parameter freigeben, die sonst möglicherweise nur in der Vorlage der übergeordneten Gruppe erstellt werden.<br /><br /> Dieses Attribut ist optional und erhält automatisch den Wert `false`, wenn es nicht enthalten ist.<br /><br /> Eingeführt in Visual Studio 2013 Update 2. Informationen zur richtigen Produktversion finden Sie unter [Referenzassemblys, die im Visual Studio 2013 SDK Update 2 bereitgestellt](https://msdn.microsoft.com/library/42b65c3e-e42b-4c39-98c8-bea285f25ffb)werden.|

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[ProjectCollection](../extensibility/projectcollection-element-visual-studio-templates.md)|Legt die Organisation und den Inhalt von Vorlagen für mehrere Projekte fest.|
|[SolutionFolder](../extensibility/solutionfolder-element-visual-studio-templates.md)|Gruppiert Projekte in Vorlagen für mehrere Projekte.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 Dieser Text gibt den Pfad zur *.vstemplate-Datei* der Vorlage an.

## <a name="remarks"></a>Bemerkungen
 Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Das `ProjectTemplateLink` Element wird verwendet, um den Speicherort der *.vstemplate-Datei* für eines der Projekte in der Vorlage anzugeben. Die *.vstemplate-Datei* einer Vorlage mit `ProjectTemplateLink` mehreren Projekten enthält ein Element für jedes Projekt in der Vorlage. Weitere Informationen zu Vorlagen mit mehreren Projekten finden Sie unter [Gewusst wie: Erstellen von Vorlagen für mehrere Projekte](../ide/how-to-create-multi-project-templates.md).

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
            <ProjectTemplateLink ProjectName="My Class Library" CopyParameters="true">
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
