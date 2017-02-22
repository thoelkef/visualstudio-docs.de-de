---
title: "Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Vorlagen mit mehreren Projekten"
  - "Projektvorlagen, Erstellen von Vorlagen mit mehreren Projekten"
  - "Visual Studio-Vorlagen, Erstellen von Vorlagen mit mehreren Projekten"
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte.  Wenn ein auf einer Vorlage mit mehreren Projekten basierendes Projekt mithilfe des Dialogfelds **Neues Projekt** erstellt wird, werden der Projektmappe alle in der Vorlage enthaltenen Projekte hinzugefügt.  
  
 Eine Vorlage mit mehreren Projekten muss die folgenden Elemente enthalten, die in eine ZIP\-Datei komprimiert werden:  
  
-   Eine VSTEMPLATE\-Stammdatei für die gesamte Vorlage mit mehreren Projekten.  Diese VSTEMPLATE\-Stammdatei enthält die im Dialogfeld **Neues Projekt** angezeigten Metadaten und gibt an, wo die VSTEMPLATE\-Dateien für die Projekte in dieser Vorlage zu finden sind.  Diese Datei muss sich im Stammverzeichnis der ZIP\-Datei befinden.  
  
-   Mindestens ein Ordner mit den Dateien, die für eine vollständige Projektvorlage erforderlich sind.  Dies schließt alle Codedateien für das Projekt sowie eine VSTEMPLATE\-Datei für das Projekt ein.  
  
 Die ZIP\-Datei einer Vorlage mit mehreren Projekten, die zwei Projekte umfasst, kann beispielsweise folgende Dateien und Verzeichnisse aufweisen:  
  
 MultiProjectTemplate.vstemplate  
  
 \\Project1\\Project1.vstemplate  
  
 \\Project1\\Project1.vbproj  
  
 \\Project1\\Class.vb  
  
 \\Project2\\Project2.vstemplate  
  
 \\Project2\\Project2.vbproj  
  
 \\Project2\\Class.vb  
  
 Die VSTEMPLATE\-Stammdatei einer Vorlage mit mehreren Projekten unterscheidet sich wie folgt von einer Vorlage mit einem einzelnen Projekt:  
  
-   Das `Type`\-Attribut des `VSTemplate`\-Elements enthält den Wert `ProjectGroup`.  Beispiele:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="ProjectGroup"  
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    ```  
  
-   Das `TemplateContent`\-Element enthält ein `ProjectCollection`\-Element mit mindestens einem `ProjectTemplateLink`\-Element, das die Pfade zu den VSTEMPLATE\-Dateien der eingeschlossenen Projekte definiert.  Beispiele:  
  
    ```  
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
  
 Vorlagen mit mehreren Projekten verhalten sich außerdem anders als normale Vorlagen.  Vorlagen mit mehreren Projekten haben die folgenden eindeutigen Merkmale:  
  
-   Einzelnen Projekten, die in einer Vorlage mit mehreren Projekten enthalten sind, können über das Dialogfeld **Neues Projekt** keine Namen zugewiesen werden.  Verwenden Sie stattdessen das `ProjectName`\-Attribut im `ProjectTemplateLink`\-Element, um den Namen für jedes Projekt anzugeben.  Weitere Informationen finden Sie im ersten Beispiel des folgenden Abschnitts.  
  
-   Vorlagen mit mehreren Projekten können Projekte enthalten, die in verschiedenen Programmiersprachen geschrieben wurden. Trotzdem kann die gesamte Vorlage mit dem `ProjectType`\-Element nur einer einzigen Kategorie zugewiesen werden.  
  
### So erstellen Sie eine Vorlage mit mehreren Projekten  
  
1.  Erstellen Sie die Projekte, die in die Vorlage mit mehreren Projekten aufgenommen werden sollen.  
  
2.  Erstellen Sie die VSTEMPLATE\-Dateien für jedes Projekt.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md).  
  
3.  Erstellen Sie eine VSTEMPLATE\-Stammdatei, die die Metadaten für die Vorlage mit mehreren Projekten enthalten soll.  Weitere Informationen finden Sie im ersten Beispiel des folgenden Abschnitts.  
  
4.  Wählen Sie die in die Vorlage aufzunehmenden Dateien und Ordner aus, klicken Sie mit der rechten Maustaste, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP\-komprimierten Ordner**.  Die Dateien und Ordner werden in eine ZIP\-Datei komprimiert.  
  
5.  Legen Sie die ZIP\-Datei der Vorlage im Projektvorlagenverzeichnis von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ab.  Standardmäßig ist dies das Verzeichnis " \\ Eigene Dateien \\ Visual Studio *Version*\\ Templates \\ ProjectTemplates \\ ".  
  
## Beispiel  
 In diesem Beispiel wird eine einfache VSTEMPLATE\-Stammdatei mit mehreren Projekten veranschaulicht.  In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`.  Durch das `ProjectName`\-Attribut im `ProjectTemplateLink`\-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird.  Wenn das `ProjectName`\-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE\-Datei als Projektname verwendet.  
  
```  
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
  
## Beispiel  
 In diesem Beispiel wird das `SolutionFolder`\-Element verwendet, um die Projekte in die folgenden beiden Gruppen zu unterteilen: `Math Classes` und `Graphics Classes`.  Die Vorlage umfasst vier Projekte, von denen jeweils zwei in einem Projektmappenordner enthalten sind.  
  
```  
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
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Gewusst wie: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder\-Element \(Visual Studio\-Vorlagen\)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink\-Element \(Visual Studio\-Vorlagen\)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)