---
title: Hinzufügen von Verzeichnissen zum Dialog Feld "Neues Element hinzufügen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f370d208cb8f7aad88f806983983ccee9f584625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68203930"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Im folgenden Codebeispiel wird veranschaulicht, wie ein neuer Satz von Verzeichnissen für das Dialogfeld **Neues Element hinzufügen** registriert wird. Verzeichnisse für das Dialogfeld **Neues Element hinzufügen** unterscheiden sich für jedes Projekt. Daher werden die Verzeichnisse unter dem Unterschlüssel projects registriert, der in enthalten ist \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects> :  
  
## <a name="the-registry-script"></a>Das Registrierungs Skript  
  
```  
NoRemove Projects  
{  
  NoRemove %GUID_Project%  
  {  
    NoRemove AddItemTemplates  
    {  
      NoRemove TemplateDirs  
      {  
        ForceRemove %CLSID_Package%  
        {  
      ForceRemove /1 = s '#%Folder_Label_ResID%'  
          {  
            val TemplatesDir = s '%Template_Path%'     
            val SortPriority = d 2000  
          }  
        }  
      }  
    }  
  }  
}  
```  
  
 Der Template_Path Wert gibt den vollständigen Pfad des Verzeichnisses an, das die Projektvorlagen enthält. Diese Vorlagen können entweder VSZ-Dateien oder prototypische Vorlagen Dateien sein, die geklont werden sollen.  
  
 Der SortPriority-Wert gibt eine Sortier Priorität an.  
  
## <a name="adding-items-to-an-existing-project"></a>Hinzufügen von Elementen zu einem vorhandenen Projekt  
 Sie können auch einem vorhandenen Projekt Elemente hinzufügen. Für ein- [!INCLUDE[csprcs](../../includes/csprcs-md.md)] Projekt können Sie z \<root> . b. dem Ordner \Programme\Microsoft Visual Studio \VC # \csharpprojectitems\localprojectitems Elemente hinzufügen. In diesem Fall `%GUID_Project%` ist die GUID für ein c#-Projekt ({FAE04EC0-301F-11d3-BF4B-00C04F79EFBC}).  
  
 Sie können ein vorhandenes Projekt auch erweitern, indem Sie einen Projekt Untertyp programmieren. Mit einem Projekt Untertyp können Sie ein Projekt erweitern, ohne einen neuen Projekttyp schreiben zu müssen. Weitere Informationen zu Projekt Untertypen finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Hinzufügen von Elementen zu den Dialog Feldern "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Projekt“](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
