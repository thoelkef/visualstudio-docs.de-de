---
title: ProjectItem-Element (Visual Studio-Elementvorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6826440ed12e90f1ffced63dfef45bb3d86177ac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701874"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem-Element (Visual Studio-Elementvorlagen)
Gibt eine Datei an, die in der Elementvorlage enthalten ist.

> [!NOTE]
> Das `ProjectItem` Element akzeptiert unterschiedliche Attribute, je nachdem, ob die Vorlage für ein Projekt oder ein Element ist. In diesem `ProjectItem` Thema wird das Element für Element erläutert. Eine Erläuterung des `ProjectItem` Elements für Projektvorlagen finden Sie unter [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md).

 \<VSTemplate \<> TemplateContent> \<ProjectItem>

## <a name="syntax"></a>Syntax

```
<ProjectItem
    SubType="Form/Component/CustomControl/UserControl"
    CustomTool="string"
    ItemType="string"
    ReplaceParameters="true/false"
    TargetFileName="TargetFileName.ext">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Attribute und Elemente
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.

### <a name="attributes"></a>Attribute

| attribute | BESCHREIBUNG |
|---------------------| - |
| `SubType` | Optionales Attribut.<br /><br /> Gibt den Untertyp eines Elements in einer Elementvorlage mit mehreren Dateien an. Dieser Wert wird verwendet, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] um den Editor zu bestimmen, der zum Öffnen des Elements verwendet wird. |
| `CustomTool` | Optionales Attribut.<br /><br /> Legt das CustomTool für das Element in der Projektdatei fest. |
| `ItemType` | Optionales Attribut.<br /><br /> Legt den ItemType für das Element in der Projektdatei fest. |
| `ReplaceParameters` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element Parameterwerte enthält, die ersetzt werden müssen, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`. |
| `TargetFileName` | Optionales Attribut.<br /><br /> Gibt den Namen des Elements an, das aus der Vorlage erstellt wird. Dieses Attribut ist nützlich, um die Parameterersetzung zum Erstellen eines Elementnamens zu verwenden. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage an.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 A, `string` das den Namen einer Datei in der *.zip-Datei* der Vorlage darstellt.

## <a name="remarks"></a>Bemerkungen
 `ProjectItem`ist ein optionales untergeordnetes Element von `TemplateContent`.

 Das `TargetFileName` Attribut kann verwendet werden, um Dateien mit Parametern umzubenennen. Wenn z. B. die Datei *MyFile.vb* im Stammverzeichnis der *.zip-Datei* der Vorlage vorhanden ist, die Datei jedoch basierend auf dem Dateinamen benannt werden soll, der vom Benutzer im Dialogfeld Neues **Element** hinzufügen bereitgestellt wird, verwenden Sie den folgenden XML-Code:

```xml
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>
```

 Wenn ein Element aus dieser Vorlage erstellt wird, basiert der Dateiname auf dem Namen, den der Benutzer im Dialogfeld **Neues Element** hinzufügen eingegeben hat. Dies ist nützlich, wenn Sie Vorlagen für Elemente mit mehreren Dateien erstellen. Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-multi-file-item-templates.md) mit mehreren Dateien und [Vorlagenparametern](../ide/template-parameters.md).

## <a name="example"></a>Beispiel
 Im folgenden Beispiel werden die Metadaten für [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] die Standardelementvorlage für eine Klasse veranschaulicht.

```
<VSTemplate Type="Item" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>MyClass</Name>
        <Description>My custom C# class.</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
        <DefaultName>MyClass.cs</DefaultName>
    </TemplateData>
    <TemplateContent>
        <ProjectItem ReplaceParameters="true">MyClass.cs</ProjectItem>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
