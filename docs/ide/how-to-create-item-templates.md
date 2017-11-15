---
title: 'Vorgehensweise: Erstellen von Elementvorlagen | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ecd17694e65c6273f8e73a321a72bc209038922
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-item-templates"></a>Gewusst wie: Erstellen von Elementvorlagen
Anhand der Schritte im [ersten Verfahren](../ide/how-to-create-item-templates.md#export_template) dieses Themas wird gezeigt, wie Sie eine Elementvorlage mithilfe des Assistenten zum **Exportieren von Vorlagen** erstellen können. Wenn Ihre Vorlage mehrere Dateien enthalten soll, finden Sie unter [Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md) entsprechende Informationen dazu.  

 Der Assistent nimmt Ihnen einen Großteil der Arbeit beim Erstellen der Standardvorlage ab, in vielen Fällen müssen Sie die VSTEMPLATE-Datei jedoch manuell bearbeiten, nachdem Sie die Vorlage exportiert haben. Wenn z.B. das Element im Dialogfeld **Neues Element hinzufügen** für ein [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-App-Projekt angezeigt werden soll, müssen Sie einige zusätzliche Schritte ausführen. Im [zweiten Verfahren](../ide/how-to-create-item-templates.md#modify_template) in diesem Thema wird beschrieben, wie Sie diese Aufgabe ausführen.  

 Informationen dazu, wie Sie angeben können, dass die Vorlage nur für bestimmte Projektuntertypen wie Office, Datenbank oder Web, angezeigt wird finden Sie in [diesem Abschnitt](#enable_templates).  

 In einigen Fällen möchten oder müssen Sie eine Elementvorlage ggf. manuell von Grund auf neu erstellen. Im [dritten Verfahren](../ide/how-to-create-item-templates.md#create_template) wird dies erläutert.  

 Informationen zu Elementen, die in der VSTEMPLATE-Datei verwendet werden können, finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md).  

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>So fügen Sie dem Dialogfeld "Neues Element hinzufügen" eine benutzerdefinierte Projektelementvorlage hinzu  

1.  Erstellen oder öffnen Sie ein Projekt in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  

2.  Fügen Sie dem Projekt ein Element hinzu, und ändern Sie dieses bei Bedarf.  

3.  Ändern Sie die Codedatei, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen finden Sie unter [Vorgehensweise: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).  

4.  Klicken Sie im Menü **Projekt** auf **Vorlage exportieren**.  

5.  Klicken Sie auf **Elementvorlage**, wählen Sie das Projekt aus, das das Element enthält, und klicken Sie auf **Weiter**.  

6.  Wählen Sie das Element aus, für das Sie eine Vorlage erstellen möchten, und klicken Sie auf **Weiter**.  

7.  Wählen Sie die Assemblyverweise aus, die in die Vorlage eingeschlossen werden sollen, und klicken Sie auf **Weiter**.  

8.  Geben Sie den Symboldateinamen, das Vorschaubild, den Vorlagennamen und die Vorlagenbeschreibung ein, und klicken Sie auf **Fertig stellen**.  

     Die Dateien für die Vorlage werden einer ZIP-Datei hinzugefügt und in das von Ihnen im Dialogfeld angegebene Verzeichnis kopiert. Der Standardspeicherort ist der Ordner **..\Benutzer\\<Benutzername\>\Dokumente\Visual Studio \<Version>\Meine exportierten Vorlagen\\**.  

    > [!WARNING]
    >  In älteren Version von Visual Studio ist der Standardspeicherort **..\Benutzer\\<Benutzername\>\Dokumente\Visual Studio \<Version>\Templates\ItemTemplates**.  

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>So aktivieren Sie die Elementvorlage, die in einem Store-Projekt verwendet werden soll  

1.  Führen Sie die Schritte in dem obenstehenden Verfahren aus, um eine Elementvorlage exportieren.  

2.  Extrahieren Sie die .vstemplate-Datei aus der ZIP-Datei, die in den Ordner „..\Benutzer\\*Benutzername*\Dokumente\Visual Studio *Version*\Templates\Itemtemplates\“ (oder **Meine exportierten Vorlagen**) kopiert wurde.  

3.  Öffnen Sie die VSTEMPLATE-Datei in Visual Studio.  

4.  Fügen Sie für ein Windows C#-Projekt in der VSTEMPLATE-Datei den folgenden XML-Code innerhalb des öffnenden `<TemplateData>`-Tags ein: `<TemplateID>Microsoft.CSharp.Class</TemplateID>`. 

    Fügen Sie für ein Windows 8.1 Store-Projekt in C# in der VSTEMPLATE-Datei den folgenden XML-Code innerhalb des öffnenden und des schließenden `<TemplateData>`-Tags ein: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.  

    Ein Windows 8.1 Store-Projekt in C++ verwendet den Wert von `WinRT-Native-6.3`. Informationen zu Windows 10- und anderen Projekttypen finden Sie unter [TemplateGroupID-Element (Visual Studio-Vorlagen)](../extensibility/templategroupid-element-visual-studio-templates.md).  

    Das folgende Beispiel zeigt den gesamten Inhalt einer VSTEMPLATE-Datei an, nachdem die XML-Zeile `<TemplateGroupID>WinRT-Managed</TemplateGroupID>` hinzugefügt wurde. Dieses Beispiel gilt für C#-Projekte. Sie können die <ProjectTpe>- und \<[TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)>-Elemente ändern, um andere Sprachen- und Projekttypen anzugeben.  

    ```xml  
    <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
      <TemplateData>  
        <DefaultName>MyItemStoreTemplate.xaml</DefaultName>  
        <Name>MyItemStoreTemplate</Name>  
        <Description>This is an example itemtemplate</Description>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>10</SortOrder>  
        <Icon>__TemplateIcon.ico</Icon>  
        <TemplateGroupID>WinRT-Managed</TemplateGroupID>  
      </TemplateData>  
      <TemplateContent>  
        <References />  
        <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>  
        <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>  
      </TemplateContent>  
    </VSTemplate>  
    ```  

     Weitere mögliche TemplateGroupID-Werte finden Sie unter [TemplateGroupID-Element (Visual Studio-Vorlagen)](../extensibility/templategroupid-element-visual-studio-templates.md). Die vollständige Referenz zu VSTEMPLATE-Dateien finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)  

5.  Speichern Sie in Visual Studio die VSTEMPLATE-Datei , und schließen Sie sie.  

6.  Kopieren Sie die .vstemplate-Datei, und fügen Sie sie wieder in die ZIP-Datei ein, die sich im Ordner „..\Benutzer\\*Benutzername*\Dokumente\Visual Studio *Version*\Templates\ItemTemplates\“ befindet.  

     Wenn das Dialogfeld **Datei kopieren** angezeigt wird, wählen Sie die Option **Kopieren und ersetzen** aus.  

 Sie können nun ein Element auf der Grundlage dieser Vorlage einem [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)]-Projekt hinzufügen, indem Sie das Dialogfeld **Neues Element hinzufügen** verwenden.  

 Weitere Informationen zu Parameternamen finden Sie unter [Vorlagenparameter](../ide/template-parameters.md).  
  
 
### <a name="enable_templates"></a> So aktivieren Sie die Vorlagen für bestimmte Projektuntertypen  

1.  In der Entwicklungsumgebung können Sie Projektelemente aus dem Dialogfeld „Element hinzufügen“ für bestimmte Projekte verfügbar machen. Verwenden Sie dieses Verfahren, um benutzerdefinierte Elemente für Windows-, Web-, Office- oder Datenbankprojekte verfügbar zu machen.  

     Suchen Sie nach dem ProjectType-Element in der VSTEMPLATE-Datei für die Elementvorlage.  

     Fügen Sie ein [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md)-Element unmittelbar nach dem ProjectType-Element hinzu.  

2.  Legen Sie den Textwert des Elements auf einen der folgenden Werte fest:  

    1.  Windows  

    2.  Office  

    3.  Datenbank  

    4.  Web  

     Beispiel: `<ProjectSubType>Database</ProjectSubType>`.  

     Im folgenden Beispiel wird eine für Office-Projekte verfügbare Elementvorlage dargestellt.  

    ```  
    <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">  
        <TemplateData>  
            <Name>Class</Name>  
            <Description>An empty class file</Description>  
            <Icon>Class.ico</Icon>  
            <ProjectType>CSharp</ProjectType>  
            <ProjectSubType>Office</ProjectSubType>  
            <DefaultName>Class.cs</DefaultName>  
        </TemplateData>  
        <TemplateContent>  
            <ProjectItem>Class1.cs</ProjectItem>  
        </TemplateContent>  
    </VSTemplate>  

    ```  

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>So erstellen Sie eine Elementvorlage manuell ohne den Assistenten zum Exportieren von Vorlagen  

1.  Erstellen Sie ein Projekt und ein Projektelement.  

2.  Bearbeiten Sie das Projektelement solange, bis es als Vorlage gespeichert werden kann.  

3.  Ändern Sie nach Bedarf die Codedatei, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen. Weitere Informationen zu Parameterersetzungen finden Sie unter [Gewusst wie: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).

4.  Erstellen Sie eine XML-Datei, und speichern Sie sie mit der Dateinamenerweiterung „.vstemplate“ in demselben Verzeichnis wie die neue Elementvorlage.  

5.  Erstellen Sie die VSTEMPLATE-XML-Datei, um Elementvorlagen-Metadaten bereitzustellen. Weitere Informationen finden Sie unter [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md) und im Beispiel im vorherigen Abschnitt.  

6.  Speichern Sie die VSTEMPLATE-Datei, und schließen Sie sie.  

7.  Wählen Sie im Windows-Explorer die Dateien aus, die in Ihrer Vorlage enthalten sein sollen, klicken Sie mit der rechten Maustaste auf die Auswahl, klicken Sie auf „Senden an“, und klicken Sie dann auf „ZIP-komprimierten Ordner“. Die ausgewählten Dateien werden in einer ZIP-Datei komprimiert.  

8.  Kopieren Sie die ZIP-Datei, und fügen Sie sie in dem Speicherort für die Benutzerelementvorlage ein. In Visual Studio 2017 ist ..\Benutzer\\<Benutzername\>\Dokumente\Visual Studio 2017\Templates\ItemTemplates\\ das Standardverzeichnis. Weitere Informationen finden Sie unter „Gewusst wie: Suchen und Organisieren von Projekt- und Elementvorlagen“.  

## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Vorgehensweise: Erstellen von Elementvorlagen mit mehreren Dateien](../ide/how-to-create-multi-file-item-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)
