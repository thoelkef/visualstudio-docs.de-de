---
title: "Gewusst wie: Manuelles Erstellen von Webvorlagen | Microsoft Docs"
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
  - "Projektvorlagen [Visual Studio], Web"
  - "Vorlagen [Visual Studio], Web"
  - "Visual Studio-Vorlagen, Web"
  - "Webvorlagen [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
caps.handback.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Manuelles Erstellen von Webvorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das Erstellen einer Webvorlage unterscheidet sich vom Erstellen anderer Arten von Vorlagen.  Da Vorlagen für Webprojekte im Dialogfeld **Neue Website hinzufügen** angezeigt werden und Webprojektelemente nach Programmiersprache kategorisiert sind, muss in der VSTEMPLATE\-Datei die Vorlage als Webvorlage gekennzeichnet sowie die Programmiersprache angegeben werden.  
  
> [!NOTE]
>  Webvorlagen müssen eine leere WEBPROJ\-Datei enthalten, die über das `File`\-Attribut des `Project`\-Elements festgelegt wird.  Obwohl für Webprojekte keine Projektdateien erforderlich sind, muss diese Datei vorhanden sein, damit eine Webvorlage einwandfrei funktioniert.  
  
### So erstellen Sie eine Webvorlage manuell  
  
1.  Erstellen Sie ein Webprojekt.  
  
2.  Ändern oder löschen Sie die Dateien im Projekt, oder fügen Sie dem Projekt neue Dateien hinzu.  
  
3.  Erstellen Sie eine XML\-Datei, und speichern Sie diese mit der Erweiterung ".vstemplate" im selben Verzeichnis wie das Projekt.  Fügen Sie die Datei nicht dem Projekt [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] hinzu.  
  
4.  Bearbeiten Sie die XML\-Datei mit der Erweiterung .vstemplate, um Metadaten für die Projektvorlage bereitzustellen.  Weitere Informationen finden Sie im Beispiel im folgenden Abschnitt.  
  
5.  Suchen Sie das `ProjectType`\-Element in der VSTEMPLATE\-Datei, und legen Sie den Textwert auf `Web` fest.  
  
6.  Fügen Sie nach dem `ProjectType`\-Element ein `ProjectSubType`\-Element ein, und geben Sie als Textwert die Programmiersprache der Vorlage an.  Die Programmiersprache kann einem der folgenden Werte entsprechen:  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Beispiele:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Wählen Sie die Dateien in der Vorlage \(einschließlich der VSTEMPLATE\-Datei\) aus, klicken Sie mit der rechten Maustaste, klicken Sie auf **Senden an**, und klicken Sie dann auf **ZIP\-komprimierten Ordner**.  Die Dateien werden in eine ZIP\-Datei komprimiert.  
  
8.  Legen Sie die ZIP\-Datei der Vorlage im Projektvorlagenverzeichnis von [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ab.  Standardmäßig ist dies das Verzeichnis " \\ Eigene Dateien \\ Visual Studio *Version*\\ My Exported Templates \\ ".  
  
## Beispiel  
 Im folgenden Beispiel wird eine grundlegende VSTEMPLATE\-Datei für eine Webprojektvorlage veranschaulicht.  
  
```  
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
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio\-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)