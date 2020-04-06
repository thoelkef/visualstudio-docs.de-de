---
title: Hinzufügen von Verzeichnissen zum neuen Projektdialogfeld | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- New Project dialog box, extending
ms.assetid: 53b328f5-20bb-49a3-bf9e-1818f4fbdf50
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 827e383bba13c9742deb654bf3d680adeb3c109b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710248"
---
# <a name="add-directories-to-the-new-project-dialog-box"></a>Hinzufügen von Verzeichnissen zum Dialogfeld Neues Projekt
Wenn Sie neue Projekttypen erstellen, können Sie auch ein neues Verzeichnis im Dialogfeld **Neues Projekt** registrieren, um es für die Verwendung als Vorlagen anzuzeigen. Im folgenden Codebeispiel wird erläutert, wie Ein neues Verzeichnis registriert wird, das auch als Knoten bezeichnet wird. Im Beispiel werden Vorlagen registriert, die vom VSPackage *CLSID_Package*verfügbar gemacht werden. Daher bietet die linke Seite des Dialogfelds **Neues Projekt** den hinzugefügten Knoten mit einem Namen, der durch die *Folder_Label_ResID* Ressource bestimmt wird. Diese Ressource wird aus der VSPackage-Satelliten-DLL geladen.

 Der **Ordnerwert** stellt eine GUID eines Ordners dar, unter dem der *Folder_Label_ResID* Knoten angezeigt wird. Im Beispiel stellt die GUID den Ordner **Andere Projekte** im Bereich **Projekttypen** des Dialogfelds **Neues Projekt** dar. Wenn der Wert **"Andere Projekte"** nicht vorhanden ist, wird die Beschriftung auf der obersten Ebene positioniert.

 Der `TemplatesDir` Wert gibt den vollständigen Pfad des Verzeichnisses an, das die Projektvorlagen enthält. Diese Dateien können entweder *.vsz* Dateien oder typische Vorlagendateien geklont werden.

 Wenn Sie `TemplatesLocalizedSubDir`angeben, muss es sich um die Ressourcen-ID einer Zeichenfolge handelt, die das Unterverzeichnis benennt, in `TemplatesDir` dem lokalisierte Vorlagen enthalten sind. Da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Zeichenfolgenressource aus einer Satelliten-DLL geladen wird, wenn Sie über eine enthält, kann jede Satelliten-DLL einen anderen Unterverzeichnisnamen enthalten. Der `SortPriority` Wert gibt eine Sortierpriorität an.

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

## <a name="see-also"></a>Weitere Informationen
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Hinzufügen von Verzeichnissen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-directories-to-the-add-new-item-dialog-box.md)
