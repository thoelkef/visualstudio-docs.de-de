---
title: ProjectItem-Element (Visual Studio-Projektvorlagen) | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84fb371460bc697660e176ca9df4c984d2b234bf
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438370"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem-Element (Visual Studio-Projektvorlagen)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Gibt eine Datei, die in der Projektvorlage enthalten ist.  
  
> [!NOTE]
> Die `ProjectItem` -Element akzeptiert verschiedene Attribute je nachdem, ob die Vorlage für ein Projekt oder ein Element. In diesem Thema wird erläutert, die `ProjectItem` -Element für Projektvorlagen. Eine Erläuterung der `ProjectItem` -Element für Elementvorlagen finden Sie unter [ProjectItem-Element (Visual Studio-Elementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<Project>  
 \<ProjectItem>  
  
## <a name="syntax"></a>Syntax  
  
```  
<ProjectItem  
    TargetFileName="TargetFileName.ext"  
    ReplaceParameters="true/false"  
    OpenInEditor="true/false"  
    OpenInWebBrowser="true/false"  
    OpenInHelpBrowser="true/false"  
    OpenOrder="Value">  
        FileName.ext  
</ProjectItem>  
```  
  
## <a name="attributes-and-elements"></a>Attribute und Elemente  
 In den folgenden Abschnitten werden attribute-Elemente sowie untergeordnete und übergeordnete Elemente beschrieben.  
  
### <a name="attributes"></a>Attribute  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen und Pfad des Projektelements an, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut ist hilfreich beim Erstellen einer Verzeichnisstruktur unterscheidet die Verzeichnisstruktur, in der ZIP-Vorlagendatei, und für die Verwendung von parameterersetzungen erstellen Sie einen Elementnamen ein.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element Parameterwerte verfügt, die ersetzt werden muss, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`sein.|  
|`OpenInEditor`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element soll, im entsprechenden Editor in geöffnet werden [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Die `OpenInWebBrowser` und `OpenInHelpBrowser` Attribute werden ignoriert, auf ein Element mit einem `OpenInEditor` Wert `true`.<br /><br /> Der Standardwert ist `false`.|  
|`OpenInWebBrowser`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element den Webbrowser geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die für das Projekt lokal sind, können in einem Webbrowser geöffnet werden. Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`.|  
|`OpenInHelpBrowser`|Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element im Hilfe-Viewer geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die für das Projekt lokal sind, können im Browser Hilfe geöffnet werden. Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`.|  
|`OpenOrder`|Optionales Attribut.<br /><br /> Gibt einen numerischen Wert für die Reihenfolge an, dass die Elemente in ihre entsprechenden Editoren geöffnet werden. Alle Werte müssen ein Vielfaches von 10 sein. Elemente mit höheren `OpenOrder` Werte zuerst geöffnet werden.|  
  
### <a name="child-elements"></a>Untergeordnete Elemente  
 Keine  
  
### <a name="parent-elements"></a>Übergeordnete Elemente  
  
|Element|Beschreibung|  
|-------------|-----------------|  
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Gibt an, die Dateien oder Verzeichnisse dem Projekt hinzu.|  
  
## <a name="text-value"></a>Textwert  
 Ein Textwert ist erforderlich.  
  
 Ein `string` , der Name oder Pfad zu einer Datei in der ZIP-Vorlagendatei darstellt.  
  
## <a name="remarks"></a>Hinweise  
 `ProjectItem` ist ein optionales untergeordnetes Element des `Project`.  
  
 Die `TargetFileName` -Attribut kann verwendet werden, um eine Verzeichnisstruktur unterscheidet die Verzeichnisstruktur erstellen, in der ZIP-Vorlagendatei. Z. B. wenn die Datei `MyFile.vb` vorhanden ist, im Stammverzeichnis der ZIP-Vorlagendatei, aber die Datei in ein Verzeichnis namens platziert werden soll `CustomFiles` in allen Projekten, die aus der Vorlage erstellt werden, verwenden Sie den folgenden XML-Code:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Die `TargetFileName` Attribut kann auch verwendet werden, um Dateien umzubenennen, die internationale Zeichen im Dateinamen enthalten. Beispielsweise kann keine ZIP-Vorlagendatei Dateinamen mit Unicode-Zeichen enthalten, damit die Datei umbenannt werden muss, bevor es in eine ZIP-Datei komprimiert werden kann. Die `TargetFileName` Attribut kann verwendet werden, um den Dateinamen wieder in den ursprünglichen Namen der Unicode-Datei festgelegt.  
  
 Die `TargetFileName` Attribut kann auch zum Umbenennen von Dateien mit Parametern verwendet werden. Das folgende Verfahren erläutert, wie Sie die Datei umbenennen `MyFile.vb`, die im Stammverzeichnis der ZIP-Vorlagendatei, basierend auf den Namen des Projekts zu einer Datei vorhanden ist.  
  
### <a name="to-rename-files-with-parameters"></a>Zum Umbenennen von Dateien mit Parametern  
  
1. Verwenden Sie das folgende XML, in der VSTEMPLATE-Datei:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2. Öffnen Sie die Projektdatei (.vbproj für ein [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] Projekt) in einem Text-Editor oder [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
3. Suchen Sie die Zeile, in der Projektdatei, die die folgenden XML-Code ähnelt:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4. Ersetzen Sie die Zeile des Codes, durch das folgende XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Wenn ein Projekt aus dieser Vorlage erstellt wird, der Dateiname wird auf Grundlage der Name des Benutzers im der **neues Projekt** Dialogfelds mit der alle unsicheren Zeichen sowie Leerzeichen entfernt wurden. Weitere Informationen finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
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
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>  
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
 [Vorlagenparameter](../ide/template-parameters.md)   
 [ProjectItem-Element (Visual Studio-Projektelementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
