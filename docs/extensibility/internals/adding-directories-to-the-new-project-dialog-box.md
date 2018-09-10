---
title: Hinzufügen von Verzeichnissen, um das Dialogfeld Neues Projekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5c8686a34f52c7dc2e6c96b602811d7e12a6a7e6
ms.sourcegitcommit: 1c2ed640512ba613b3bbbc9ce348e28be6ca3e45
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39500786"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Fügen Sie Verzeichnisse hinzu, um das Dialogfeld "Neues Projekt"
Wenn Sie neue Projekttypen erstellen, Sie auch können registrieren, ein neues Verzeichnis, in der **neues Projekt** im Dialogfeld für die Verwendung als Vorlage anzeigen. Im folgenden Codebeispiel wird erläutert, wie ein neues Verzeichnis, auch bekannt als ein Knoten registriert wird. Im Beispiel Vorlagen, die verfügbar gemacht, von dem VSPackage *CLSID_Package*, registriert sind. Als Ergebnis der linken Seite des der **neues Projekt** Dialogfeld bietet die hinzugefügten Knoten mit einem Namen, der bestimmt, indem die *Folder_Label_ResID* Ressource. Diese Ressource wird aus der Satelliten-DLL für das VSPackage geladen.  
  
 Die **Ordner** Wert darstellt, eine GUID, der einen Ordner unter dem die *Folder_Label_ResID* Knoten wird angezeigt. Im Beispiel ist die GUID darstellt der **andere Projekte** Ordner in der **Projekttypen** im Bereich der **neues Projekt** Dialogfeld. Wenn die **andere Projekte** Wert fehlt, die Bezeichnung wird auf der obersten Ebene positioniert.  
  
 Die `TemplatesDir` Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Dateien können es sich entweder *VSZ* Dateien oder typische Vorlagendateien, geklont zu werden.  
  
 Bei Angabe von `TemplatesLocalizedSubDir`, es muss eine Zeichenfolge, die das Unterverzeichnis des Namen der Ressourcen-ID `TemplatesDir` , lokalisierte Vorlagen enthält. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] lädt die Zeichenfolgenressource aus einer Satelliten-DLL, wenn Sie über eine Ressourcengruppe verfügen jedes Satelliten-DLL kann einen anderen Unterverzeichnisnamen enthalten. Die `SortPriority` Wert gibt an, eine Sortierung Priorität.  
  
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
 [Fügen Sie Elemente hinzu, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Fügen Sie Verzeichnisse hinzu, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)