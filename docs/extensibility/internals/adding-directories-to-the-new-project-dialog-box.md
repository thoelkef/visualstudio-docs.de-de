---
title: Hinzufügen von Verzeichnissen auf das neue Projekt (Dialogfeld) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 13
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload:
- vssdk
ms.openlocfilehash: 881979b54fb8f8f07a7ffeb2f3648b690fe2bf78
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Hinzufügen von Verzeichnissen auf das neue Projekt (Dialogfeld)
Bei der Erstellung des neuen Projekttypen werden Sie auch können registrieren ein neues Verzeichnisses in der **neues Projekt** (Dialogfeld), um diese als Vorlagen für die Verwendung anzuzeigen. Im folgenden Codebeispiel wird erläutert, wie ein neues Verzeichnis, auch bekannt als einen Knoten zu registrieren. Im Beispiel werden die Vorlagen, die vom VSPackage CLSID_Package registriert. Als Ergebnis der linken Seite des der **neues Projekt** Dialogfeld bietet den hinzugefügten Knoten mit einem Namen, die von der Ressource Folder_Label_ResID bestimmt. Diese Ressource wird aus der VSPackage-Satelliten-DLL geladen.  
  
 Die **Ordner** Wert stellt eine GUID für einen Ordner unter dem der Folder_Label_ResID Knoten angezeigt wird. Im Beispiel stellt die GUID der **andere Projekte** Ordner in der **Projekttypen** im Bereich der **neues Projekt** (Dialogfeld). Wenn die **andere Projekte** Wert vorhanden ist, die Bezeichnung befindet sich auf der obersten Ebene.  
  
 Der TemplatesDir-Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Dateien können .vsz-Dateien oder typische Vorlagendateien zu klonenden sein.  
  
 Wenn Sie TemplatesLocalizedSubDir angeben, muss es die Ressourcen-ID, der eine Zeichenfolge sein, das Unterverzeichnis des TemplatesDir benennt, die lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt eine Zeichenfolgenressource aus der Satelliten-DLL, wenn Sie haben jedes Satelliten-DLL darf eine andere Unterverzeichnisnamen. Der SortPriority-Wert gibt eine Sortierung Priorität.  
  
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
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)