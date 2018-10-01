---
title: 'Vorgehensweise: Manuelles Erstellen von Webvorlagen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4d84a71d54f178574e7aba719f4189b35312ec03
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520638"
---
# <a name="how-to-manually-create-web-templates"></a>Gewusst wie: Manuelles Erstellen von Webvorlagen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Vorgehensweise: Web-Vorlagen manuell erstellen](https://docs.microsoft.com/visualstudio/ide/how-to-manually-create-web-templates).  
  
Das Erstellen einer Webvorlage unterscheidet sich vom Erstellen anderer Vorlagen. Da Vorlagen für Webprojekte im Dialogfeld **Neue Website hinzufügen** angezeigt werden, und Elemente von Webprojekten nach Programmiersprache kategorisiert werden, muss die Vorlage in der VSTEMPLATE-Datei als Webvorlage angegeben sein. Die Datei muss außerdem Angaben zur Programmiersprache enthalten.  
  
> [!NOTE]
>  Webvorlagen müssen eine leere WEBPROJ-Datei enthalten, die mithilfe des `File`-Attributs des `Project`-Elements angegeben wird. Obwohl Webprojekte keine Projektdateien benötigen, ist diese Datei erforderlich, damit eine Webvorlage richtig funktioniert.  
  
### <a name="to-manually-create-a-web-template"></a>So erstellen Sie eine Webvorlage manuell  
  
1.  Erstellen Sie ein Webprojekt.  
  
2.  Ändern Sie die Dateien im Projekt, oder löschen Sie sie. Alternativ können Sie auch neue Dateien zum Projekt hinzufügen.  
  
3.  Erstellen Sie eine XML-Datei, und speichern Sie sie mit der Erweiterung VSTEMPLATE in demselben Verzeichnis wie das Projekt. Fügen Sie sie nicht zum Projekt in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] hinzu.  
  
4.  Erstellen Sie die VSTEMPLATE-XML-Datei, um Projektvorlagenmetadaten bereitzustellen. Weitere Informationen finden Sie im Beispiel im folgendem Abschnitt.  
  
5.  Suchen Sie das `ProjectType`-Element in der VSTEMPLATE-Datei, und legen den Textwert auf `Web` fest.  
  
6.  Fügen Sie nach dem `ProjectType`-Element ein `ProjectSubType`-Element hinzu, und legen Sie den Textwert auf die Programmiersprache der Vorlage fest. Die Programmiersprache kann einer der folgenden sein:  
  
    -   CSharp  
  
    -   Visual Basic  
  
     Zum Beispiel:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Wählen Sie die Dateien in der Vorlage aus (einschließlich der VSTEMPLATE-Datei), klicken Sie mit der rechten Maustaste auf die Auswahl, klicken Sie auf **Send To** (Senden an) und anschließend auf **Compressed (zipped) Folder** (ZIP-komprimierter Ordner). Die Dateien werden in eine ZIP-Datei komprimiert.  
  
8.  Platzieren die ZIP-Vorlagendatei im [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Projektvorlagenverzeichnis. Standardmäßig ist dies das Verzeichnis \Eigene Dokumente\Visual Studio *Version*\ItemTemplates\\.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird eine einfache VSTEMPLATE-Datei für eine Webprojektvorlage gezeigt.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Erstellen von Projekt- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Schemareferenz zu Visual Studio-Vorlagen](../extensibility/visual-studio-template-schema-reference.md)



