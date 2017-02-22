---
title: "Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien | Microsoft Docs"
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
  - "Elementvorlagen, Erstellen von Elementvorlagen mit mehreren Dateien"
  - "Erstellen von Elementvorlagen mit mehreren Dateien"
  - "Visual Studio-Vorlagen, Erstellen von Elementvorlagen mit mehreren Dateien"
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: 12
caps.handback.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durch Elementvorlagen wird möglicherweise nur ein Element angegeben, manchmal besteht das Element jedoch aus mehreren Dateien.  Zum Beispiel erfordert eine Windows Form\-Elementvorlage für Visual Basic die folgenden drei Dateien:  
  
-   Eine VB\-Datei, die den Code für das Formular enthält.  
  
-   Eine DESIGNER.VB\-Datei, die Designerinformationen zum Formular enthält.  
  
-   Eine RESX\-Datei, die die eingebetteten Ressourcen für das Formular enthält.  
  
 Elementvorlagen mit mehreren Dateien erfordern Parameter, um sicherzustellen, dass beim Erstellen des Elements in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] die richtigen Dateinamenerweiterungen verwendet werden.  Wenn Sie eine Elementvorlage mit dem Assistenten **Vorlage exportieren** erstellen, werden diese Parameter automatisch generiert, und es ist keine weitere Bearbeitung erforderlich.  Die folgenden Schritte zeigen, wie Sie anhand von Parametern sicherstellen, dass die richtigen Dateinamenerweiterungen erstellt werden.  
  
### So erstellen Sie eine Elementvorlage mit mehreren Dateien manuell  
  
1.  Erstellen Sie die Elementvorlage auf die gleiche Weise, wie Sie eine Elementvorlage für eine einzelne Datei erstellen.  Weitere Informationen finden Sie unter [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).  
  
2.  Fügen Sie `TargetFileName`\-Attribute zu jedem `ProjectItem`\-Element hinzu.  Legen Sie die Werte der `TargetFileName`\-Attribute auf $fileinputname$.*FileExtension* fest, wobei *FileExtension* der Dateinamenerweiterung der Datei entspricht, die in die Vorlage aufgenommen wird.  Beispiele:  
  
    ```  
    <ProjectItem TargetFileName="$fileinputname$.vb">  
        Form1.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
        Form1.Designer.vb  
    </ProjectItem>  
    <ProjectItem TargetFileName="$fileinputname$.resx">  
        Form1.resx  
    </ProjectItem>  
    ```  
  
     Wenn ein von dieser Vorlage abgeleitetes Element einem Projekt hinzugefügt wird, basieren die Dateinamen auf dem Namen, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat.  
  
3.  Wählen Sie die in die Vorlage aufzunehmenden Dateien aus, klicken Sie mit der rechten Maustaste, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP\-komprimierter Ordner**.  Die ausgewählten Dateien werden in einer ZIP\-Datei komprimiert.  
  
4.  Legen Sie die ZIP\-Datei am Speicherort der Benutzerelementvorlage ab.  Standardmäßig ist das Verzeichnis " \\ Eigene Dateien \\ Visual Studio *Version*\\ Templates \\ ItemTemplates \\.  Weitere Informationen finden Sie unter [Gewusst wie: Suchen und Organisieren von Vorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## Beispiel  
 Im folgenden Beispiel wird eine Windows Form\-Vorlage in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dargestellt.  Wenn ein Element auf der Grundlage dieser Vorlage erstellt wird, entspricht der Name der drei erstellten Dateien dem im Dialogfeld **Neues Element hinzufügen** eingegebenen Namen.  
  
```  
<VSTemplate Version="2.0.0" Type="Item"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>Multi-file Item Template</Name>  
        <Icon>Icon.ico</Icon>  
        <Description>An example of a multi-file item template</Description>  
        <ProjectType>VisualBasic</ProjectType>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem TargetFileName="$fileinputname$.vb" SubType="Form">  
            Form1.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.Designer.vb">  
            Form1.Designer.vb  
        </ProjectItem>  
        <ProjectItem TargetFileName="$fileinputname$.resx">  
            Form1.resx  
        </ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Gewusst wie: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md)