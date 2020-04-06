---
title: Beitrag zum Dialogfeld Neues Element hinzufügen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 83444d9be6ba23392b792a0187bf46dc9920c465
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709280"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Beitragen zum Dialogfeld Neues Element hinzufügen
Ein Projektuntertyp kann ein komplett neues Verzeichnis von Elementen für das Dialogfeld **Neues Element hinzufügen** bereitstellen, indem Vorlagen zum Hinzufügen von **Elementen** unter dem Unterschlüssel **"Projekte"-Registrierung** registriert werden.

## <a name="register-add-new-item-templates"></a>Registrieren zum Hinzufügen neuer Artikelvorlagen
 Dieser Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE-SOFTWARE-Microsoft-VisualStudio-Projekte** in der Registrierung. Die folgenden Registrierungseinträge [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gehen von einem Projekt aus, das von einem hypothetischen Projektuntertyp aggregiert wird. Die Einträge [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] für das Projekt sind unten aufgeführt.

```
[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}]
@="#2143"
"DefaultProjectExtension"="vbproj"
"PossibleProjectExtensions"="vbproj;vbp"
"ProjectTemplatesDir"="visualStudioInstallPath\\Vb\\.\\VBProjects"

[HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects\{F184B08F-C81C-45F6-A57F-5ABD9991F28F}\AddItemTemplates\TemplateDirs\{12345678-1234-1234-1122334455667788}\/1]
@="#100"
"TemplatesDir"="projectSubTypeTemplatesDir\\VBProjectItems"
```

 Der Unterschlüssel **AddItemTemplates-TemplateDirs** enthält Registrierungseinträge mit dem Pfad zum Verzeichnis, in dem Elemente platziert werden, die im Dialogfeld **Neues Element** hinzufügen zur Verfügung gestellt werden.

 Die Umgebung lädt automatisch alle **AddItemTemplates-Daten** unter dem Unterschlüssel **"Projekte".** Diese Daten können die Daten für Basisprojektimplementierungen sowie die Daten für bestimmte Projektuntertyptypen enthalten. Jeder Projektuntertyp wird durch eine **Projekttyp-GUID**identifiziert. Der Projektuntertyp kann angeben, dass ein alternativer Satz von Vorlagen zum **Hinzufügen** `VSHPROPID_ AddItemTemplatesGuid` von Element für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> eine bestimmte aromatisierte Projektinstanz verwendet werden soll, indem die Enumeration von in der Implementierung unterstützt wird, um den GUID-Wert des Projektsubtyps zurückzugeben. Wenn `VSHPROPID_AddItemTemplatesGuid` die Eigenschaft nicht angegeben ist, wird die Basisprojekt-GUID verwendet.

 Sie können Elemente im Dialogfeld Neues Element <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> **hinzufügen** filtern, indem Sie die Schnittstelle für das Projektsubtype-Aggregatorobjekt implementieren. Beispielsweise kann ein Projektuntertyp, der ein Datenbankprojekt [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] implementiert, indem [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] er ein Projekt aggregiert, die spezifischen Elemente aus dem Dialogfeld Neues Element `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> **hinzufügen** filtern kann, indem er Filter implementiert, und kann wiederum datenbankprojektspezifische Elemente hinzufügen, indem er in unterstützt wird. Weitere Informationen zum Filtern und Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzufügen** finden Sie unter Hinzufügen von Elementen zum [Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
