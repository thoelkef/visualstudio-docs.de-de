---
title: ProjectItem-Element (Visual Studio-Projektelementvorlagen) | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- <ProjectItem> element [Visual Studio item templates]
- ProjectItem element [Visual Studio item templates]
ms.assetid: 9ed94112-0c38-49df-b728-0dd2d0d1eb47
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 51fe9e60bf646e91b957210c43ca020b16f420c4
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515003"
---
# <a name="projectitem-element-visual-studio-item-templates"></a>ProjectItem-Element (Visual Studio-Elementvorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ProjectItem-Element (Visual Studio-Elementvorlagen)](https://docs.microsoft.com/visualstudio/extensibility/projectitem-element-visual-studio-item-templates).  
  
Gibt eine Datei, die in der Elementvorlage enthalten ist.  
  
> [!NOTE]
>  Die `ProjectItem` -Element akzeptiert verschiedene Attribute je nachdem, ob die Vorlage für ein Projekt oder ein Element. In diesem Thema wird erläutert, die `ProjectItem` -Element für Element. Eine Erläuterung der `ProjectItem` -Element für Projektvorlagen finden Sie unter [ProjectItem-Element (Visual Studio-Projektvorlagen)](../extensibility/projectitem-element-visual-studio-project-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent >  
 \<ProjectItem >  
  
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
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`SubType`|Optionales Attribut.<br /><br /> Gibt den Untertyp eines Elements in einer Elementvorlage mit mehreren Dateien an. Dieser Wert wird verwendet, um den Editor zu bestimmen, die [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verwendet, um das Element zu öffnen.|  
|`CustomTool`|Optionales Attribut.<br /><br /> Legt die CustomTool für das Element in der Projektdatei fest.|  
|`ItemType`|Optionales Attribut.<br /><br /> Legt den ItemType für das Element in der Projektdatei fest.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element Parameterwerte verfügt, die ersetzt werden muss, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`sein.|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen des Elements, das aus der Vorlage erstellt wird. Dieses Attribut ist nützlich für die Verwendung von parameterersetzungen erstellen Sie einen Elementnamen ein.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Gibt den Inhalt der Vorlage.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Ein `string` , die den Namen einer Datei in der ZIP-Vorlagendatei darstellt.  
  
## <a name="remarks"></a>Hinweise  
 `ProjectItem` ist ein optionales untergeordnetes Element des `TemplateContent`.  
  
 Die `TargetFileName` Attribut zum Umbenennen von Dateien mit Parametern verwendet werden kann. Z. B. wenn die Datei `MyFile.vb` in das Stammverzeichnis der ZIP-Datei der Vorlage, aber Sie möchten, die die Datei benannt wird auf den vom Benutzer im angegebenen Dateinamen basierend vorhanden ist die **neues Element hinzufügen** (Dialogfeld), verwenden Sie das folgende XML:  
  
```  
<ProjectItem TargetFileName="$fileinputname$.vb">MyFile.vb</ProjectItem>  
```  
  
 Wenn ein Element aus dieser Vorlage erstellt wird, der Dateiname wird auf Grundlage der Name des Benutzers im der **neues Element hinzufügen** Dialogfeld. Dies ist nützlich, beim Erstellen von Elementvorlagen mit mehreren Dateien. Weitere Informationen finden Sie unter [wie: Erstellen von mehreren Dateien Elementvorlagen](../ide/how-to-create-multi-file-item-templates.md) und [Vorlagenparameter](../ide/template-parameters.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt die Metadaten für die standard-Elementvorlage für eine [!INCLUDE[csprcs](../includes/csprcs-md.md)] Klasse.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)

