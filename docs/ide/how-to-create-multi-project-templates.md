---
title: Erstellen von Vorlagen mit mehreren Projekten für Visual Studio | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/02/2018
ms.technology:
- vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: b3902dd2b6f4dfac72d61d2c4d81937dcbbfdd07
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-create-multi-project-templates"></a>Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten

Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Wenn Sie ein Projekt über das Dialogfeld **Neues Projekt** erstellen, das auf einer Vorlage mit mehreren Projekten basiert, wird jedes Projekt in der Vorlage zur Projektmappe hinzugefügt.

Eine Vorlage mit mehreren Projekten verfügt über mindestens zwei Projektvorlagen und eine Stammvorlage des Typs `ProjectGroup`.

Vorlagen mit mehreren Projekten verhalten sich anders als Vorlagen mit einem Projekt. Sie weisen folgende eindeutige Merkmale auf:

- Einzelnen Projekten in einer Vorlage mit mehreren Projekten können im Dialogfeld **Neues Projekt** keine Namen zugewiesen werden. Verwenden Sie stattdessen das Attribut `ProjectName` des Elements `ProjectTemplateLink` in der *VSTEMPLATE*-Datei, um einen Namen für jedes Projekt anzugeben.

- Vorlagen mit mehreren Projekten können Projekte für unterschiedliche Sprachen enthalten. Die gesamte Vorlage kann jedoch nur einer einzigen Kategorie zugeordnet werden. Geben Sie die Kategorie der Vorlage im Element `ProjectType` der *VSTEMPLATE*-Datei an.

Eine Vorlage mit mehreren Projekten muss folgende in eine *ZIP*-Datei komprimierte Elemente enthalten:

- Eine *VSTEMPLATE*-Stammdatei für die gesamte Vorlage mit mehreren Projekten. Diese *VSTEMPLATE*-Stammdatei enthält Metadaten, die im Dialogfeld **Neues Projekt** angezeigt werden, und gibt an, wo sich die *VSTEMPLATE*-Dateien für die Projekte in der Vorlage befinden. Die Datei muss sich im Stamm der *ZIP*-Datei befinden.

- Für eine vollständige Projektvorlage sind mindestens zwei Ordner erforderlich, die die Dateien enthalten. Diese Ordner enthalten alle Codedateien und eine *VSTEMPLATE*-Datei für das Projekt.

Eine *ZIP*-Datei für eine Vorlage mit mehreren Projekten, die zwei Projekte enthält, kann beispielsweise folgende Dateien und Verzeichnisse enthalten:

- *MultiProjectTemplate.vstemplate*
- *\Project1\Project1.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\Project2.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

Die *VSTEMPLATE*-Stammdatei für eine Vorlage mit mehreren Projekten unterscheidet sich folgendermaßen von der für eine Vorlage mit einem einzelnen Projekt:

- Das `Type`-Attribut des `VSTemplate`-Elements weist den Wert `ProjectGroup` statt `Project` auf. Zum Beispiel:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- Das `TemplateContent`-Element enthält ein `ProjectCollection`-Element, das über mindestens ein `ProjectTemplateLink`-Element verfügt, das den Pfad der *VSTEMPLATE*-Datei der enthaltenen Projekte definiert. Zum Beispiel:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\Project1.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\Project2.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

## <a name="to-create-a-multi-project-template-from-an-existing-solution"></a>Erstellen einer Vorlage mit mehreren Projekten aus einer vorhandenen Projektmappe

1. Erstellen Sie eine Projektmappe, und fügen Sie mindestens zwei Projekte hinzu.

1. Passen Sie die Projekte an, bis diese in eine Vorlage exportiert werden können.

1. Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.

   Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.

1. Wählen Sie auf der Seite **Vorlagentyp auswählen** die Option **Projektvorlage** aus. Wählen Sie das Projekt aus, das Sie in eine Vorlage exportieren möchten, und klicken Sie anschließend auf **Weiter**.

1. Geben Sie auf der Seite **Vorlagenoptionen auswählen** einen Namen, ggf. eine Beschreibung sowie ein Symbol für Ihre Vorlage ein, und fügen Sie ein Vorschaubild hinzu. Klicken Sie auf **Fertig stellen**.

   Das Projekt wird als *ZIP*-Datei exportiert und am angegebenen Speicherort platziert.

   > [!NOTE]
   > Jedes Projekt muss separat als Vorlage exportiert werden. Wiederholen Sie die vorherigen Schritte also für jedes Projekt in der Projektmappe.

1. Erstellen Sie ein Verzeichnis für Ihre Vorlage und ein Unterverzeichnis für jedes Projekt.

1. Extrahieren Sie die Inhalte für die *ZIP*-Datei jedes Projekts in das entsprechende Unterverzeichnis, das Sie erstellt haben.

1. Erstellen Sie im Basisverzeichnis eine XML-Datei mit der Erweiterung *VSTEMPLATE*. Diese Datei enthält die Metadaten für die Vorlage mit mehreren Projekten. Im Folgenden finden Sie ein Beispiel für die Struktur der Datei. Stellen Sie sicher, dass Sie den relativen Pfad zu der *VSTEMPLATE*-Datei eines jeden Projekts angeben.

1. Wählen Sie das Basisverzeichnis aus, führen Sie einen Rechtsklick durch, oder klicken Sie auf das Kontextmenü, und wählen Sie **Senden an** > **ZIP-komprimierter Ordner** aus.

   Die Dateien und Ordner werden in eine *ZIP*-Datei komprimiert.

1. Kopieren Sie die *ZIP*-Datei in das Verzeichnis für Benutzerprojektvorlagen. Standardmäßig ist das Verzeichnis *%USERPROFILE%\Documents\Visual Studio \<Version\>\Templates\ProjectTemplates*.

1. Öffnen Sie in Visual Studio das Dialogfeld **Neues Projekt**, und stellen Sie sicher, dass Ihre Vorlage angezeigt wird.

## <a name="two-project-example"></a>Beispiel mit zwei Projekten

Dieses Beispiel zeigt eine einfache *VSTEMPLATE*-Stammdatei für mehrere Projekte. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Das `ProjectName`-Attribut des `ProjectTemplateLink`-Elements gibt den Namen an, der dem Projekt zugewiesen ist.

> [!TIP]
> Wenn das `ProjectName`-Attribut nicht angegeben ist, wird der Name der *VSTEMPLATE*-Datei als Projektname verwendet.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
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

## <a name="example-with-solution-folders"></a>Beispiel mit Projektmappenordnern

In diesem Beispiel wird das `SolutionFolder`-Element verwendet, um die Projekte in zwei Gruppen (`Math Classes` und `Graphics Classes`) zu unterteilen. Die Vorlage enthält vier Projekte, von denen sich je zwei in jedem Projektmappenordner befinden.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Siehe auch

[Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)  
[Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)  
[Visual Studio Template Schema Reference (Extensibility) (Schemareferenz zu Vorlagen für Visual Studio (Erweiterbarkeit))](../extensibility/visual-studio-template-schema-reference.md)  
[SolutionFolder-Element (Visual Studio-Vorlagen)](../extensibility/solutionfolder-element-visual-studio-templates.md)  
[ProjectTemplateLink-Element (Visual Studio-Vorlagen)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
