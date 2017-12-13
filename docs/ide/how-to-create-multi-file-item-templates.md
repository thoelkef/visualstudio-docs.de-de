---
title: 'Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, creating multi-file item templates
- multi-file item templates
- item templates, creating multi-file item templates
ms.assetid: fe3c4257-e383-4c80-b8af-c5c521959c33
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: e3e1f6c6e62494f040e2f52180c5588688f460db
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-multi-file-item-templates"></a>Gewusst wie: Erstellen von Elementvorlagen mit mehreren Dateien
Elementvorlagen können nur ein Element angeben, manchmal besteht ein Element jedoch aus mehreren Dateien. Eine Windows Forms-Elementvorlage für Visual Basic erfordert beispielsweise folgende drei Dateien:  
  
-   Eine VB-Datei, die den Code für das Formular enthält.  
  
-   Eine DESIGNER.VB-Datei, die die Designer-Informationen für das Formular enthält.  
  
-   Eine RESX-Datei, die die eingebetteten Ressourcen für das Formular enthält.  
  
 Elementvorlagen mit mehreren Dateien erfordern Parameter, um sicherzustellen, dass die richtigen Erweiterungen verwendet werden, wenn das Element in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erstellt wird. Wenn Sie eine Elementvorlage mithilfe des **Assistenten zum Exportieren von Vorlagen** erstellen, werden diese Parameter automatisch generiert, und keine weitere Bearbeitung ist erforderlich. In den folgenden Schritten wird erläutert, wie diese Parameter dafür verwendet werden, das Erstellen der richtigen Erweiterung sicherzustellen.  
  
### <a name="to-manually-create-a-multi-file-item-template"></a>Manuelles Erstellen einer Elementvorlage mit mehreren Dateien  
  
1.  Erstellen Sie die Elementvorlage wie eine Elementvorlage mit einer einzelnen Datei. Weitere Informationen finden Sie unter [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md).  
  
2.  Fügen Sie jedem `ProjectItem`-Element das `TargetFileName`-Attribut hinzu. Legen Sie die Werte des `TargetFileName`-Attributs auf „$fileinputname$.*Dateierweiterung*“ fest, wobei *Dateierweiterung* der Erweiterung der Datei entspricht, die in die Vorlage eingefügt wird. Zum Beispiel:  
  
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
  
     Wenn ein Element, das von dieser Vorlage abgeleitet wurde, zu einem Projekt hinzugefügt wird, basieren die Dateinamen auf dem Namen, den der Benutzer im Dialogfeld **Neues Element hinzufügen** eingegeben hat.  
  
3.  Wählen Sie die Dateien aus, die in die Vorlage eingefügt werden sollen, und klicken Sie mit der rechten Maustaste auf die Auswahl. Klicken Sie dann auf **Senden an** und auf **ZIP-komprimierter Ordner**. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.  
  
4.  Fügen Sie die ZIP-Datei am Speicherort der Benutzerelementvorlage ein. Standardmäßig ist dies das Verzeichnis \Eigene Dateien\Visual Studio *Version*\Templates\ItemTemplates\\. Weitere Informationen finden Sie unter [Vorgehensweise: Suchen und Organisieren von Projekt- und Elementvorlagen](../ide/how-to-locate-and-organize-project-and-item-templates.md).  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Windows Forms-Vorlage. Wenn ein Element basierend auf dieser Vorlage erstellt wird, stimmen die Namen der drei erstellten Dateien mit dem Namen überein, der im Dialogfeld **Neues Element hinzufügen** eingegeben wurde.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)   
 [Vorlagenparameter](../ide/template-parameters.md)   
 [Gewusst wie: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md)