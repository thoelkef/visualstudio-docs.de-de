---
title: "Verzeichnisse, die im Dialogfeld Neues Projekt hinzuf&#252;gen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dialogfeld "Neues Projekt", erweitern"
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 13
---
# Verzeichnisse, die im Dialogfeld Neues Projekt hinzuf&#252;gen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie neue Projekttypen erstellen, können Sie ein neues Verzeichnis im Dialogfeld **Neues Projekt** auch registrieren, um sie für die Verwendung als Vorlagen anzuzeigen.  Im folgenden Codebeispiel wird beschrieben, wie ein neues Verzeichnis, auch als einen Knoten registriert.  Im Beispiel werden die Vorlagen, die von einem VSPackage CLSID\_Package verfügbar gemacht werden, registriert.  Daher bietet die linke Seite des Dialogfelds **Neues Projekt** den hinzugefügten Knoten an, wenn ein Name von der Folder\_Label\_ResID\-Ressource spezifisch sind.  Diese Ressource wird vom VSPackage\-Satelliten DLL geladen.  
  
 Der **Ordner**\-Wert stellt eine GUID eines Ordners dar, unter dem der Folder\_Label\_ResID\-Knoten angezeigt wird.  Im Beispiel wird die GUID des **Andere Projekte** Ordner im **Projekttypen** Bereich des Dialogfelds **Neues Projekt** dar.  Wenn der **Andere Projekte**\-Wert nicht vorhanden ist, wird die Bezeichnung außerhalb oben Ebene.  
  
 Der TemplatesDir\-Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält.  Diese Dateien können entweder zu klonende .vsz\-Dateien Vorlagendateien befinden oder die typischen.  
  
 Wenn Sie TemplatesLocalizedSubDir angeben, muss er die Ressourcen\-ID einer Zeichenfolge sein, die den Namen enthält, der TemplatesDir von Unterverzeichnissen Vorlagen lokalisierten.  Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Zeichenfolgenressource aus einem Satelliten\-DLL lädt, wenn Sie ein haben, kann jeder Satelliten\-DLLs einen anderen Namen der Unterverzeichnisse enthalten. Der SortPriority\-Wert gibt eine Sortierpriorität an.  
  
```  
NoRemove NewProjectTemplates  
{  
    NoRemove TemplateDirs  
  {  
    ForceRemove %CLSID_Package%  
    {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
      {  
        val Folder = s '{DCF2A94A-45B0-11D1-ADBF-00C04FB6BE4C}'  
        val TemplatesDir = s '%Template_Path%'  
        val TemplatesLocalizedSubDir = s '#100'  
        val SortPriority = d 1000  
      }  
    }  
  }  
}  
```  
  
## Siehe auch  
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)