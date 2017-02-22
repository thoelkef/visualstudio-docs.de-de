---
title: "ProjectItem-Element (Visual Studio-Projektvorlagen) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem>-Element [Visual Studio-Projektvorlagen]"
  - "ProjectItem-Element [Visual Studio-Projektvorlagen]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem-Element (Visual Studio-Projektvorlagen)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gibt eine Datei an, die in der Projektvorlage enthalten ist.  
  
> [!NOTE]
>  Je nachdem, ob die Vorlage für ein Projekt oder ein Element entwickelt wurde, akzeptiert das `ProjectItem`\-Element verschiedene Attribute.  In diesem Thema wird das `ProjectItem`\-Element für Projektvorlagen erläutert.  Eine Erläuterung des `ProjectItem`\-Elements für Elementvorlagen finden Sie unter [ProjectItem\-Element \(Visual Studio\-Elementvorlagen\)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
## Syntax  
  
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
  
## Attribute und Elemente  
 In den folgenden Abschnitten werden Attribute, untergeordnete Elemente und übergeordnete Elemente beschrieben.  
  
### Attribute  
  
|Attribut|Description|  
|--------------|-----------------|  
|`TargetFileName`|Optionales Attribut.<br /><br /> Gibt den Namen und Pfad des Projektelements an, wenn ein Projekt von der Vorlage erstellt wird.  Dieses Attribut ist hilfreich beim Erstellen einer Verzeichnisstruktur, die sich von der Verzeichnisstruktur in der ZIP\-Datei der Vorlage unterscheidet, oder beim Erstellen des Elementnamens mittels Parameterersetzung.|  
|`ReplaceParameters`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den angegeben wird, ob das Element über Parameterwerte verfügt, die ersetzt werden müssen, wenn ein Projekt von der Vorlage erstellt wird.  Der Standardwert lautet `false`.|  
|`OpenInEditor`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den festgelegt wird, ob das Element beim Erstellen eines Projekts von der Vorlage in seinem zugewiesenen Editor in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] geöffnet wird.<br /><br /> Das `OpenInWebBrowser`\-Attribut und das `OpenInHelpBrowser`\-Attribut werden bei einem Element mit dem `OpenInEditor`\-Wert `true` ignoriert.<br /><br /> Der Standardwert ist `false`.|  
|`OpenInWebBrowser`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den angegeben wird, ob das Element im Webbrowser geöffnet werden soll, wenn ein Projekt von der Vorlage erstellt wird.<br /><br /> Nur lokal im Projekt vorhandene HTML\- und Textdateien können im Webbrowser geöffnet werden.  Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`.|  
|`OpenInHelpBrowser`|Optionales Attribut.<br /><br /> Ein boolescher Wert, durch den angegeben wird, ob das Element im Hilfe\-Viewer geöffnet werden soll, wenn ein Projekt von der Vorlage erstellt wird.<br /><br /> Nur lokal im Projekt vorhandene HTML\- und Textdateien können im Hilfebrowser geöffnet werden.  Externe URLs können nicht mit diesem Attribut geöffnet werden.<br /><br /> Der Standardwert ist `false`.|  
|`OpenOrder`|Optionales Attribut.<br /><br /> Gibt einen numerischen Wert für die Reihenfolge an, in der Elemente in den zugewiesenen Editoren geöffnet werden.  Alle Werte müssen ein Vielfaches von 10 sein.  Elemente mit höheren `OpenOrder`\-Werten werden zuerst geöffnet.|  
  
### Untergeordnete Elemente  
 Keine.  
  
### Übergeordnete Elemente  
  
|Element|Description|  
|-------------|-----------------|  
|[Project](../extensibility/project-element-visual-studio-templates.md)|Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.|  
  
## Textwert  
 Ein Textwert ist erforderlich.  
  
 `string` mit dem Namen oder Pfad zu einer Datei, die in der ZIP\-Datei der Vorlage enthalten ist.  
  
## Hinweise  
 `ProjectItem` ist ein optionales untergeordnetes Element von `Project`.  
  
 Das `TargetFileName`\-Attribut kann zum Erstellen einer Verzeichnisstruktur verwendet werden, die sich von der Verzeichnisstruktur in der ZIP\-Datei der Vorlage unterscheidet.  Wenn die Datei `MyFile.vb` im Stammverzeichnis der ZIP\-Datei der Vorlage vorhanden ist, sie jedoch in allen von der Vorlage erstellten Projekten in einem Verzeichnis mit dem Namen `CustomFiles` abgelegt werden soll, würden Sie beispielsweise folgenden XML\-Code verwenden:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 Über das `TargetFileName`\-Attribut können zudem Dateien mit internationalen Zeichen im Dateinamen umbenannt werden.  Eine als Vorlage verwendete ZIP\-Datei kann beispielsweise keine Dateinamen mit Unicode\-Zeichen enthalten. Die Datei muss daher umbenannt werden, bevor sie in einer ZIP\-Datei komprimiert werden kann.  Über das `TargetFileName`\-Attribut kann der Dateiname auf den ursprünglichen Unicode\-Dateinamen zurückgesetzt werden.  
  
 Das `TargetFileName`\-Attribut kann auch dazu verwendet werden, Dateien mit Parametern umzubenennen.  Im Folgenden wird beschrieben, wie Sie die im Stammverzeichnis der ZIP\-Vorlagendatei enthaltene Datei `MyFile.vb` auf der Grundlage des Projektnamens umbenennen.  
  
### So benennen Sie Dateien mit Parametern um  
  
1.  Verwenden Sie in der VSTEMPLATE\-Datei die folgende XML:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Öffnen Sie die Projektdatei \(VBPROJ für ein [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Projekt\) in einem Text\-Editor oder [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Suchen Sie die Zeile in der Projektdatei, die ähnlich aussieht wie die folgende XML:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Ersetzen Sie die Codezeile durch die folgende XML:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Wenn ein Projekt von dieser Vorlage erstellt wird, basiert der Dateiname auf dem Namen, den der Benutzer im Dialogfeld **Neues Projekt** eingegeben hat. Unsichere Zeichen sowie Leerzeichen werden aus dem Namen entfernt.  Weitere Informationen finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
## Beispiel  
 Im folgenden Beispiel werden die Metadaten für eine Projektvorlage einer [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)]\-Anwendung veranschaulicht.  
  
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
  
## Siehe auch  
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [ProjectItem\-Element \(Visual Studio\-Elementvorlagen\)](../extensibility/projectitem-element-visual-studio-item-templates.md)