---
title: 'Vorgehensweise: Erstellen von Vorlagen mit mehreren Projekten | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-project templates
- project templates, creating multi-project templates
- multi-project templates
ms.assetid: 8c7f7065-137e-40ad-868d-37e007270efd
caps.latest.revision: "16"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: ac7701e3e4dc11bc5634436c3e6f831f6711e514
ms.sourcegitcommit: 03a74d29a1e0584ff4808ce6c9e812b51e774905
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2018
---
# <a name="how-to-create-multi-project-templates"></a>Gewusst wie: Erstellen von Vorlagen mit mehreren Projekten
Vorlagen mit mehreren Projekten fungieren als Container für mindestens zwei Projekte. Wenn ein Projekt über das Dialogfeld **Neues Projekt** erstellt wird, das auf einer Vorlage mit mehreren Projekten basiert, wird jedes Projekt in der Vorlage zur Projektmappe hinzugefügt.  

 Eine Vorlage mit mehreren Projekten besteht aus zwei oder mehreren Projektvorlagen und einer Stammvorlage des Typs `ProjectGroup`.

 Vorlagen mit mehreren Projekten verhalten sich anders als normale Vorlagen. Vorlagen mit mehreren Projekten weisen folgende eindeutige Merkmale auf:  
  
-   Einzelnen Projekten in einer Vorlage mit mehreren Projekten können keine Namen über das Dialogfeld **Neues Projekt** zugewiesen werden. Verwenden Sie stattdessen das `ProjectName`-Attribut des `ProjectTemplateLink`-Elements, um den Namen für jedes Projekt anzugeben. Weitere Informationen finden Sie im ersten Beispiel im folgenden Abschnitt.  
  
-   Vorlagen mit mehreren Projekten können Projekte enthalten, die in unterschiedlichen Sprachen geschrieben sind. Die gesamte Vorlage kann jedoch nur einer einzigen Kategorie zugeordnet werden, indem das `ProjectType`-Element verwendet wird.  
  
### <a name="to-create-a-multi-project-template"></a>Erstellen einer Vorlage mit mehreren Projekten  
  
1.  Erstellen Sie die Projekte, die in der Vorlage mit mehreren Projekten enthalten sein sollen:
    1.  Erstellen eines Projekts.  
  
    > [!NOTE]
    >  Verwenden Sie nur gültige Bezeichnerzeichen beim Benennen eines Projekts, das als Quelle für eine Vorlage verwendet wird. Eine aus einem Projekt exportierte Vorlage, das mit ungültigen Zeichen benannt wurde, kann in zukünftigen Projekten, die auf dieser Vorlage basieren, Kompilierungsfehler verursachen. Weitere Informationen zu gültigen Bezeichnerzeichen finden Sie unter [Declared Element Names (Namen deklarierter Elemente)](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
    2.  Bearbeiten Sie das Projekt solange, bis es als Vorlage exportiert werden kann.  
  
    3.  Ändern Sie gegebenenfalls die Codedateien, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen zu Parameterersetzungen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).  
  
    4.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**. Der **Assistent zum Exportieren von Vorlagen** wird geöffnet.  
  
    5.  Klicken Sie auf **Projektvorlage**.  
  
    6.  Wenn sich in Ihrer aktuellen Projektmappe mehr als ein Projekt befindet, müssen Sie das Projekt auswählen, das Sie als Vorlage exportieren möchten.  
  
    7.  Klicken Sie auf **Weiter**.  
  
    8.  Wählen Sie ein Symbol und ein Vorschaubild für die Vorlage aus. Diese werden im Dialogfeld **Neues Projekt** angezeigt.  
  
    9. Geben Sie einen Namen und eine Beschreibung für die Vorlage ein.  
  
    10. Klicken Sie auf **Fertig stellen**. Das Projekt wird als ZIP-Datei exportiert und am angegebenen Speicherort platziert. Außerdem wird es in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importiert, wenn diese Option ausgewählt wurde.  
  
2.  Extrahieren Sie die VSTEMPLATE-Datei aus der generierten ZIP-Datei im selben Verzeichnis wie die Projektdatei, mit der die Vorlage exportiert wurde.

3.  Erstellen Sie eine VSTEMPLATE-Stammdatei, die die Metadaten für die Vorlage mit mehreren Projekten enthalten soll. Weitere Informationen finden Sie im ersten Beispiel im folgenden Abschnitt.  
  
4.  Wählen Sie die Dateien und Ordner aus, die in der Vorlage enthalten sein sollen, klicken Sie mit der rechten Maustaste auf die Auswahl, klicken Sie auf **Senden an** und dann auf **ZIP-komprimierten Ordner**. Die Dateien und Ordner werden in eine ZIP-Datei komprimiert.  
  
> [HINWEIS!] Eine Vorlage mit mehreren Projekten muss folgende in eine ZIP-Datei komprimierte Elemente enthalten:  
>   
> -   Eine VSTEMPLATE-Stammdatei für die gesamte Vorlage mit mehreren Projekten. Diese VSTEMPLATE-Stammdatei enthält die Metadaten, die im Dialogfeld **Neues Projekt** angezeigt werden, und gibt an, wo sich die VSTEMPLATE-Dateien für die Projekte in dieser Vorlage befinden. Die Datei muss sich im Stamm der ZIP-Datei befinden.  
>   
> -   Für eine vollständige Projektvorlage sind ein oder mehrere Ordner erforderlich, die die Dateien enthalten. Dies schließt alle Codedateien und eine VSTEMPLATE-Datei für das Projekt ein.  
>   
> Eine ZIP-Datei für eine Vorlage mit mehreren Projekten, die zwei Projekte enthält, kann beispielsweise folgende Dateien und Verzeichnisse enthalten:  
>   
>  MultiProjectTemplate.vstemplate  
>   
>  \Project1\Project1.vstemplate  
>   
>  \Project1\Project1.vbproj  
>   
>  \Project1\Class.vb  
>   
>  \Project2\Project2.vstemplate  
>   
>  \Project2\Project2.vbproj  
>   
>  \Project2\Class.vb  
>   
>  Die VSTEMPLATE-Stammdatei für eine Vorlage mit mehreren Projekten unterscheidet sich folgendermaßen von der für eine Vorlage mit einem einzelnen Projekt:  
>   
> -   Das `Type`-Attribut des `VSTemplate`-Elements enthält den Wert `ProjectGroup`. Zum Beispiel:  
>   
>     ```  
>     <VSTemplate Version="2.0.0" Type="ProjectGroup"  
>         xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
>     ```  
>   
> -   Das `TemplateContent`-Element enthält ein `ProjectCollection`-Element, das ein oder mehrere `ProjectTemplateLink`-Elemente besitzt, die den Pfad der VSTEMPLATE-Datei der enthaltenen Projekte definiert. Zum Beispiel:  
>   
>     ```  
>     <TemplateContent>  
>         <ProjectCollection>  
>             <ProjectTemplateLink>  
>                 Project1\Project1.vstemplate  
>             </ProjectTemplateLink>  
>             <ProjectTemplateLink>  
>                 Project2\Project2.vstemplate  
>             </ProjectTemplateLink>  
>         </ProjectCollection>  
>     </TemplateContent>  
>     ```  
>   
  
5.  Platzieren die ZIP-Vorlagendatei im [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Projektvorlagenverzeichnis. Standardmäßig ist dies das Verzeichnis \Eigene Dateien\Visual Studio *Version*\Templates\ProjectTemplates\\.  
  
## <a name="example"></a>Beispiel  
 Dieses Beispiel zeigt eine einfache VSTEMPLATE-Stammdatei für mehrere Projekte. In diesem Beispiel enthält die Vorlage zwei Projekte: `My Windows Application` und `My Class Library`. Durch das `ProjectName`-Attribut im `ProjectTemplateLink`-Element wird der Name festgelegt, der dem Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] zugewiesen wird. Wenn das `ProjectName`-Attribut nicht vorhanden ist, wird der Name der VSTEMPLATE-Datei als Projektname verwendet.  
  
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
  
## <a name="example"></a>Beispiel  
 In diesem Beispiel wird das `SolutionFolder`-Element verwendet, um die Projekte in zwei Gruppen (`Math Classes` und `Graphics Classes`) zu unterteilen. Die Vorlage enthält vier Projekte, von denen sich je zwei in jedem Projektmappenordner befinden.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [Vorgehensweise: Erstellen von Projektvorlagen](../ide/how-to-create-project-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)   
 [SolutionFolder-Element (Visual Studio-Vorlagen)](../extensibility/solutionfolder-element-visual-studio-templates.md)   
 [ProjectTemplateLink-Element (Visual Studio-Vorlagen)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)
