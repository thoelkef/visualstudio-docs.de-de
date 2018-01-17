---
title: "Erstellen einer Webvorlage für Visual Studio | Microsoft-Dokumentation"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f94823131e568b3f1f254ead9d760210a4c9c1e0
ms.sourcegitcommit: 9357209350167e1eb7e50b483e44893735d90589
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/05/2018
---
# <a name="how-to-manually-create-web-templates"></a>Vorgehensweise: Manuelles Erstellen von Webvorlagen

Das Erstellen einer Webvorlage unterscheidet sich vom Erstellen anderer Vorlagen. Da Vorlagen für Webprojekte im Dialogfeld **Neue Website hinzufügen** angezeigt werden, und Elemente von Webprojekten nach Programmiersprache kategorisiert werden, muss die Vorlage in der VSTEMPLATE-Datei als Webvorlage angegeben sein. Die Datei muss außerdem Angaben zur Programmiersprache enthalten.

> [!NOTE]
> Webvorlagen müssen eine leere WEBPROJ-Datei und einen Verweis in der VSTEMPLATE-Datei im `File`-Attribut des `Project`-Elements enthalten. Zwar erfordern Webprojekte keine \*PROJ-Projektdatei, jedoch ist es notwendig, diese Stub-Datei zu erstellen, damit die Webvorlage einwandfrei funktionieren kann.

### <a name="to-manually-create-a-web-template"></a>So erstellen Sie eine Webvorlage manuell

1. Erstellen Sie ein Webprojekt.

1. Ändern Sie die Dateien im Projekt, oder löschen Sie sie. Alternativ können Sie auch neue Dateien zum Projekt hinzufügen.

1. Erstellen Sie eine XML-Datei, und speichern Sie sie mit der Erweiterung VSTEMPLATE in demselben Verzeichnis wie das Projekt. Fügen Sie sie nicht zu dem Projekt in Visual Studio hinzu.

1. Bearbeiten Sie die VSTEMPLATE-XML-Datei, um Metadaten für Projektvorlagen bereitzustellen. Weitere Informationen finden Sie im [folgenden Beispiel](#example).

1. Suchen Sie das `ProjectType`-Element in der VSTEMPLATE-Datei, und legen den Textwert auf `Web` fest.

1. Fügen Sie nach dem `ProjectType`-Element ein `ProjectSubType`-Element hinzu, und legen Sie den Textwert auf die Programmiersprache der Vorlage fest. Die Programmiersprache kann einer der folgenden sein:

    - CSharp
    - Visual Basic

    Zum Beispiel:

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. Wählen Sie die Dateien in der Vorlage aus (einschließlich der VSTEMPLATE-Datei), klicken Sie mit der rechten Maustaste auf die Auswahl, und klicken Sie anschließend auf **Senden an** > **ZIP-komprimierter Ordner**. Die Dateien werden in eine ZIP-Datei komprimiert.

1. Legen Sie die ZIP-Vorlagendatei im Visual Studio-Projektvorlagenverzeichnis ab. Standardmäßig handelt es sich dabei um das Verzeichnis „%USERPROFILE%\Documents\Visual Studio \<Version\>\ProjectTemplates“.

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird eine einfache VSTEMPLATE-Datei für eine Webprojektvorlage dargestellt:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple Web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch

[Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  
[Visual Studio Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md)