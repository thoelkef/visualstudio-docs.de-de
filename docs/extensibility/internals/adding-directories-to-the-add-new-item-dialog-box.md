---
title: Hinzufügen von Verzeichnissen, die im Dialogfeld Neues Element hinzufügen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 981b65df9354277580ee1c816f4e0fd0977f9a85
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328015"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Fügen Sie Verzeichnisse hinzu, um das Dialogfeld "Neues Element hinzufügen"
Im folgenden Codebeispiel wird veranschaulicht, wie zum Registrieren einer neuen Gruppe von Verzeichnissen, für die **neues Element hinzufügen** Dialogfeld. Verzeichnisse für die **neues Element hinzufügen** Dialogfeld unterscheiden sich für die einzelnen Projekte. Aus diesem Grund werden die Verzeichnisse unter registriert die **Projekte** finden Sie im Unterschlüssel **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0Exp\Projects**.

## <a name="registry-script"></a>Registrierungsskript

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

 Die `%Template_Path%` Wert gibt den vollständigen Pfad des Verzeichnisses, das die Projektvorlagen enthält. Diese Vorlagen können es sich entweder *VSZ* Dateien oder prototypischen Vorlagendateien, geklont zu werden.

 Die `SortPriority` Wert gibt an, eine Sortierung Priorität.

## <a name="add-items-to-an-existing-project"></a>Hinzufügen von Elementen zu einem vorhandenen Projekt
 Sie können auch Elemente zu einem vorhandenen Projekt hinzufügen. Z. B. für eine [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] -Projekt können Sie Elemente zum Hinzufügen der  *\<Stamm > \Programme\Microsoft Visual Studio\VC#\CSharpProjectItems\LocalProjectItems* Ordner. In diesem Fall `%GUID_Project%` ist die GUID für ein C#-Projekt ({FAE04EC0-301F-11D3-BF4B-00C04F79EFBC}).

 Sie können auch ein vorhandenes Projekt erweitern, indem Sie die Programmierung von einem Projektuntertyp. Mit einem Projektuntertyp können Sie ein Projekt erweitern, ohne einen neuen Projekttyp schreiben zu müssen. Weitere Informationen zu Projektuntertypen, finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Siehe auch
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Fügen Sie Elemente hinzu, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Fügen Sie Verzeichnisse hinzu, um das Dialogfeld "Neues Projekt"](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)