---
title: "Gewusst wie: Erstellen von Projektvorlagen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.ExportTemplateWizard"
helpviewer_keywords: 
  - "Projektvorlagen, Erstellen"
  - "Projektvorlagen, Speicherorte für benutzerdefinierte Vorlagen"
  - "Projektvorlagen, Metadatendateien"
  - "Visual Studio-Vorlagen, Erstellen von Projektvorlagen"
  - "Visual Studio-Vorlagen, Projektvorlagen"
ms.assetid: a1a6999d-a34c-48a8-b1cf-027eb5c76398
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Gewusst wie: Erstellen von Projektvorlagen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Mit der folgenden Prozedur können Sie eine Vorlage mithilfe des Assistenten **Vorlage exportieren** erstellen, der die Vorlage in einer ZIP\-Datei verpackt.  Sie können Vorlagen im VSIX\-Dateiformat für eine Bereitstellung auch erstellen, indem Sie den Assistenten zum Exportieren von Vorlagenen\-Erweiterung oder mit den Vorlagen verwenden, die in [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]einbezogen werden, oder Sie können Vorlagen manuell erstellen.  
  
### So erstellen Sie eine benutzerdefinierte Projektvorlage mit dem standardmäßigen Assistenten "Vorlage exportieren"  
  
1.  Erstellen Sie ein Projekt.  
  
    > [!NOTE]
    >  Verwenden Sie zum Benennen eines Projekts, das als Quelle für eine Vorlage dient, nur gültige Bezeichnerzeichen.  Eine Vorlage, die aus einem mit ungültigen Zeichen benannten Projekt exportiert wird, kann zu Kompilierungsfehlern bei zukünftigen Projekten führen, die auf der Vorlage basieren.  Weitere Informationen über gültige Bezeichnerzeichen finden Sie unter [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names).  
  
2.  Bearbeiten Sie das Projekt, bis es als Vorlage exportiert werden kann.  
  
3.  Bearbeiten Sie ggf. die Codedateien, um anzugeben, an welcher Stelle Parameterersetzungen stattfinden sollen.  Weitere Informationen zur Parameterersetzung finden Sie unter [Gewusst wie: Ersetzen von Parametern in einer Vorlage](../ide/how-to-substitute-parameters-in-a-template.md).  
  
4.  Klicken Sie im Menü **Datei** auf **Vorlage exportieren**.  Der Assistent **Vorlage exportieren** wird geöffnet.  
  
5.  Klicken Sie auf **Projektvorlage**.  
  
6.  Wenn die aktuelle Projektmappe mehrere Projekte enthält, wählen Sie die Projekte aus, die Sie in eine Vorlage exportieren möchten.  
  
7.  Klicken Sie auf **Next**.  
  
8.  Wählen Sie ein Symbol und ein Vorschaubild für die Vorlage aus.  Dieses werden im Dialogfeld **Neues Projekt** angezeigt.  
  
9. Geben Sie einen Vorlagennamen und eine Beschreibung ein.  
  
10. Klicken Sie auf **Fertig stellen**.  Das Projekt wird in eine ZIP\-Datei exportiert, im angegebenen Ausgabeverzeichnis eingefügt und, falls aktiviert, nach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] importiert.  
  
     Wenn [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] installiert ist, können Sie die fertige Vorlage mit der Vorlage **VSIX Project** zur Bereitstellung in eine VSIX\-Datei einbinden.  Weitere Informationen finden Sie unter [Erste Schritte mit der VSIX\-Projektvorlage](../extensibility/getting-started-with-the-vsix-project-template.md).  
  
## Siehe auch  
 [Erstellen von benutzerdefinierten Projekt\- und Elementvorlagen](../ide/creating-project-and-item-templates.md)   
 [Gewusst wie: Erstellen von Elementvorlagen](../ide/how-to-create-item-templates.md)