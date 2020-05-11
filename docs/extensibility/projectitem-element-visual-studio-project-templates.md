---
title: ProjectItem-Element (Visual Studio-Projektvorlagen) | Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701842"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>ProjectItem-Element (Visual Studio-Projektvorlagen)
Gibt eine Datei an, die in der Projektvorlage enthalten ist.

> [!NOTE]
> Das `ProjectItem` Element akzeptiert unterschiedliche Attribute, je nachdem, ob die Vorlage für ein Projekt oder ein Element ist. In diesem `ProjectItem` Thema wird das Element für Projektvorlagen erläutert. Eine Erläuterung des `ProjectItem` Elements für Elementvorlagen finden Sie unter [ProjectItem Element (Visual Studio Item Templates)](../extensibility/projectitem-element-visual-studio-item-templates.md).

 \<VSTemplate \<> TemplateContent \< \<> Project> ProjectItem>

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

| attribute | BESCHREIBUNG |
|---------------------| - |
| `TargetFileName` | Optionales Attribut.<br /><br /> Gibt den Namen und Pfad des Projektelements an, wenn ein Projekt aus der Vorlage erstellt wird. Dieses Attribut ist nützlich, um eine Verzeichnisstruktur zu *.zip* erstellen, die sich von der Verzeichnisstruktur in der ZIP-Datei der Vorlage unterscheidet, oder um die Parameterersetzung zum Erstellen eines Elementnamens zu verwenden. |
| `ReplaceParameters` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element Parameterwerte enthält, die ersetzt werden müssen, wenn ein Projekt aus der Vorlage erstellt wird. Der Standardwert ist `false`. |
| `OpenInEditor` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Element in seinem jeweiligen Editor geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Die `OpenInWebBrowser` `OpenInHelpBrowser` und-Attribute werden für ein `OpenInEditor` Element `true`mit dem Wert von ignoriert.<br /><br /> Der Standardwert ist `false`. |
| `OpenInWebBrowser` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element im Webbrowser geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die lokal im Projekt sind, können im Webbrowser geöffnet werden. Externe URLs können mit diesem Attribut nicht geöffnet werden.<br /><br /> Der Standardwert ist `false`. |
| `OpenInHelpBrowser` | Optionales Attribut.<br /><br /> Ein boolescher Wert, der angibt, ob das Element im Hilfe-Viewer geöffnet werden soll, wenn ein Projekt aus der Vorlage erstellt wird.<br /><br /> Nur HTML-Dateien und Textdateien, die lokal im Projekt sind, können im Hilfebrowser geöffnet werden. Externe URLs können mit diesem Attribut nicht geöffnet werden.<br /><br /> Der Standardwert ist `false`. |
| `OpenOrder` | Optionales Attribut.<br /><br /> Gibt einen numerischen Wert an, der die Reihenfolge darstellt, in der Elemente in den jeweiligen Editoren geöffnet werden. Alle Werte müssen ein Vielfaches von 10 sein. Elemente mit `OpenOrder` höheren Werten werden zuerst geöffnet. |

### <a name="child-elements"></a>Untergeordnete Elemente
 Keine.

### <a name="parent-elements"></a>Übergeordnete Elemente

|Element|BESCHREIBUNG|
|-------------|-----------------|
|[Projekt](../extensibility/project-element-visual-studio-templates.md)|Gibt die Dateien oder Verzeichnisse an, die dem Projekt hinzugefügt werden sollen.|

## <a name="text-value"></a>Textwert
 Ein Textwert ist erforderlich.

 A, `string` das den Namen oder Pfad zu einer Datei in der *ZIP-Datei* der Vorlage darstellt.

## <a name="remarks"></a>Bemerkungen
 `ProjectItem`ist ein optionales untergeordnetes Element von `Project`.

 Das `TargetFileName` Attribut kann verwendet werden, um eine Verzeichnisstruktur zu erstellen, die sich von der Verzeichnisstruktur in der *.zip-Datei* der Vorlage unterscheidet. Wenn z. B. die Datei *MyFile.vb* im Stammverzeichnis der *.zip-Datei* der Vorlage vorhanden ist, die Datei jedoch in allen Projekten, die aus der Vorlage erstellt wurden, in einem Verzeichnis mit dem Namen *CustomFiles* abgelegt werden soll, verwenden Sie den folgenden XML-Code:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 Das `TargetFileName` Attribut kann auch verwendet werden, um Dateien umzubenennen, die internationale Zeichen in ihren Dateinamen enthalten. Beispielsweise kann eine *.zip-Vorlagedatei* keine Dateinamen mit Unicode-Zeichen enthalten, daher muss die Datei umbenannt werden, bevor sie in eine *ZIP-Datei* komprimiert werden kann. Das `TargetFileName` Attribut kann verwendet werden, um den Dateinamen wieder auf den ursprünglichen Unicode-Dateinamen festzulegen.

 Das `TargetFileName` Attribut kann auch verwendet werden, um Dateien mit Parametern umzubenennen. Im folgenden Verfahren wird erläutert, wie Sie die Datei *MyFile.vb*, die im Stammverzeichnis der Vorlage *ZIP-Datei* vorhanden ist, in einen Dateinamen umbenennen, der auf dem Projektnamen basiert.

### <a name="to-rename-files-with-parameters"></a>So benennen Sie Dateien mit Parametern um

1. Verwenden Sie den folgenden XML-Code in der *.vstemplate-Datei:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Öffnen Sie die Projektdatei ( [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] *.vbproj* für [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ein Projekt) in einem Texteditor oder .

3. Suchen Sie die Zeile in der Projektdatei, die dem folgenden XML ähnelt:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Ersetzen Sie die Codezeile durch den folgenden XML-Code:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Wenn ein Projekt aus dieser Vorlage erstellt wird, basiert der Dateiname auf dem Namen, den der Benutzer im Dialogfeld **Neues Projekt** eingegeben hat, wobei alle unsicheren Zeichen und Leerzeichen entfernt werden. Weitere Informationen finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).

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

## <a name="see-also"></a>Weitere Informationen
- [Visual Studio-Vorlagenschemareferenz](../extensibility/visual-studio-template-schema-reference.md)
- [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)
- [Vorlagenparameter](../ide/template-parameters.md)
- [ProjectItem-Element (Visual Studio-Elementvorlagen)](../extensibility/projectitem-element-visual-studio-item-templates.md)
