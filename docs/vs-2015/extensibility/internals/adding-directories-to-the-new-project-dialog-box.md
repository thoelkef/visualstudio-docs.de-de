---
title: Hinzufügen von Verzeichnissen, um das Dialogfeld Neues Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6a03e61cf3699cd45a7b4b8e6a7e5b7d192ca6de
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51769736"
---
# <a name="adding-directories-to-the-new-project-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Projekt“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie neue Projekttypen erstellen, Sie auch können registrieren, ein neues Verzeichnis, in der **neues Projekt** im Dialogfeld für die Verwendung als Vorlage anzeigen. Im folgenden Codebeispiel wird erläutert, wie ein neues Verzeichnis, auch bekannt als ein Knoten registriert wird. Im Beispiel werden die Vorlagen, die von VSPackages CLSID_Package verfügbar gemacht werden registriert. Als Ergebnis der linken Seite des der **neues Projekt** Dialogfeld bietet die hinzugefügten Knoten mit einem Namen, die von der Ressource Folder_Label_ResID bestimmt. Diese Ressource wird aus der Satelliten-DLL für das VSPackage geladen.  
  
 Die **Ordner** Wert darstellt, eine GUID eines Ordners an, unter denen der Folder_Label_ResID Knoten angezeigt wird. Im Beispiel ist die GUID darstellt der **andere Projekte** Ordner in der **Projekttypen** im Bereich der **neues Projekt** Dialogfeld. Wenn die **andere Projekte** Wert fehlt, die Bezeichnung wird auf der obersten Ebene positioniert.  
  
 Der TemplatesDir-Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Dateien können entweder VSZ-Dateien oder typische Vorlagendateien zu klonenden sein.  
  
 Wenn Sie TemplatesLocalizedSubDir angeben, muss sie die Ressourcen-ID einer Zeichenfolge, die das Unterverzeichnis des TemplatesDir benennt, die lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] lädt die Zeichenfolgenressource aus einer Satelliten-DLL, wenn Sie über eine Ressourcengruppe verfügen jedes Satelliten-DLL kann einen anderen Unterverzeichnisnamen enthalten. Der Wert SortPriority gibt es sich um eine Sortierung Priorität.  
  
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
 [Hinzufügen von Elementen, das Hinzufügen neuer Elemente in Dialogfeldern](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Element hinzufügen“](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)

