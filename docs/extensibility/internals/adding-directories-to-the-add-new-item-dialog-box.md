---
title: Hinzufügen von Verzeichnissen zum Dialogfeld Neues Element hinzufügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, extending
ms.assetid: 67ae8af6-3752-49e8-8ce3-007aca5f7982
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d4af79f95c87271e9a10eece6c728daa9a81305
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710249"
---
# <a name="add-directories-to-the-add-new-item-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld Neues Element hinzufügen
Im folgenden Codebeispiel wird veranschaulicht, wie Sie einen neuen Satz von Verzeichnissen für das Dialogfeld **Neues Element hinzufügen** registrieren. Verzeichnisse für das Dialogfeld **Neues Element hinzufügen** sind für jedes Projekt unterschiedlich. Daher werden die Verzeichnisse unter dem Unterschlüssel **Projekte** registriert, der sich in **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-8.0Exp-Projekte**befindet.

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

 Der `%Template_Path%` Wert gibt den vollständigen Pfad des Verzeichnisses an, das die Projektvorlagen enthält. Diese Vorlagen können entweder *.vsz-Dateien* oder prototypische Vorlagendateien geklont werden.

 Der `SortPriority` Wert gibt eine Sortierpriorität an.

## <a name="add-items-to-an-existing-project"></a>Hinzufügen von Elementen zu einem vorhandenen Projekt
 Sie können einem vorhandenen Projekt auch Elemente hinzufügen. Für ein [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] Projekt können Sie z. B. Elemente zum * \<Ordner "Root"->-Programmdateien, Microsoft Visual Studio, "CSharpProjectItems" und "LocalProjectItems"* hinzufügen. In diesem `%GUID_Project%` Fall ist die GUID für ein C-Projekt (FAE04EC0-301F-11D3-BF4B-00C04F79EFBC).

 Sie können ein vorhandenes Projekt auch erweitern, indem Sie einen Projektuntertyp programmieren. Mit einem Projektuntertyp können Sie ein Projekt erweitern, ohne einen neuen Projekttyp zu schreiben. Weitere Informationen zu Projektuntertypen finden Sie unter [Projektuntertypen](../../extensibility/internals/project-subtypes.md).

## <a name="see-also"></a>Weitere Informationen
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Hinzufügen von Verzeichnissen zum Dialogfeld Neues Projekt](../../extensibility/internals/adding-directories-to-the-new-project-dialog-box.md)
