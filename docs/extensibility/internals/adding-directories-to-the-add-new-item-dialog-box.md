---
title: Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b8d9989e8cf4ec8f0eb714a26e73d89fba339b71
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31127747"
---
# <a name="adding-directories-to-the-add-new-item-dialog-box"></a>Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen
Im folgenden Codebeispiel wird veranschaulicht, wie zum Registrieren einer neuen Gruppe von Verzeichnissen für die **neues Element hinzufügen** (Dialogfeld). Verzeichnisse für die **neues Element hinzufügen** Dialogfeld unterscheiden sich für jedes Projekt. Aus diesem Grund werden die Verzeichnisse unter dem Unterschlüssel Projekte finden registriert \<HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects >:  
  
## <a name="the-registry-script"></a>Die Registrierungsdatei  
  
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
  
 Der Template_Path-Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Vorlagen möglich .vsz-Dateien oder prototypischen Vorlagendateien zu klonenden.  
  
 Der SortPriority-Wert gibt eine Sortierung Priorität.  
  
## <a name="adding-items-to-an-existing-project"></a>Hinzufügen von Elementen zu einem vorhandenen Projekt  
 Sie können Elemente auch zu einem vorhandenen Projekt hinzufügen. Z. B. für eine [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -Projekt können Sie Elemente zum Hinzufügen der \<Stamm > Ordner "\Programme\Microsoft Visual Studio \VC#\CSharpProjectItems\LocalProjectItems". In diesem Fall die `%GUID_Project%` ist die GUID für ein C#-Projekt ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).  
  
 Sie können auch ein vorhandenes Projekt erweitern, indem ein Projektuntertyp-Programmierung. Mit einem Projektuntertyp können Sie ein Projekt erweitern, ohne einen neuen Projekttyp schreiben zu müssen. Weitere Informationen zum Projekt Untertypen, finden Sie unter [Projekt Untertypen](../../extensibility/internals/project-subtypes.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Hinzufügen von Verzeichnissen zum Dialogfeld „Neues Projekt“](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)