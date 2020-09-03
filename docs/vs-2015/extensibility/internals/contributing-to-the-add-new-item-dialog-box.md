---
title: Beitrag zum Dialog Feld "Neues Element hinzufügen" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d288f2d007fd0f923021847179326069959d3698
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197026"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Mitwirken am Dialogfeld „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ein Projekt Untertyp kann ein neues Element Verzeichnis für das Dialogfeld **Neues Element hinzufügen** bereitstellen, indem **Sie Add Element** Templates unter dem `Projects` Registrierungs Unterschlüssel registrieren.  
  
## <a name="registering-add-new-item-templates"></a>Registrieren von Add New Item Templates  
 Dieser Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE \software\microsoft\visualstudio\8.0\Projects** in der Registrierung. In den folgenden Registrierungs Einträgen wird davon ausgegangen, dass ein [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt durch einen hypothetischen Projekt Untertyp aggregiert wird. Die Einträge für das [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt sind unten aufgeführt.  
  
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
  
 Der `AddItemTemplates\TemplateDirs` Unterschlüssel enthält Registrierungseinträge mit dem Pfad zum Verzeichnis, in dem Elemente, die im Dialogfeld **Neues Element hinzufügen** verfügbar gemacht wurden, platziert werden.  
  
 Die Umgebung lädt automatisch alle `AddItemTemplates` Daten unter dem `Projects` Registrierungs Unterschlüssel. Dies kann die Daten für Basisprojekt Implementierungen sowie die Daten für bestimmte Projekt Untertypen Typen enthalten. Jeder Projekt Untertyp wird durch einen Projekttyp identifiziert `GUID` . Der Projekt Untertyp kann angeben, dass ein alternativer Satz von `Add Item` Vorlagen für eine bestimmte Projekt Instanz verwendet werden soll, indem die `VSHPROPID_ AddItemTemplatesGuid` Enumeration von in der Implementierung unterstützt wird <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> , um den GUID-Wert des Projekt unter Typs zurückzugeben. Wenn `VSHPROPID_AddItemTemplatesGuid` Property nicht angegeben wird, wird die Basisprojekt-GUID verwendet.  
  
 Sie können Elemente im Dialogfeld **Neues Element hinzufügen** filtern, indem Sie die- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Schnittstelle für das Projekt Untertyp-Aggregator-Objekt implementieren. Beispielsweise kann ein Projekt Untertyp, der ein Datenbankprojekt durch das aggregierten eines [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekts implementiert, die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] bestimmten Elemente im Dialogfeld **Neues Element hinzufügen** filtern, indem Sie Filter implementiert und wiederum Datenbankprojekt spezifische Elemente hinzufügen, indem Sie in unterstützt `VSHPROPID_ AddItemTemplatesGuid` <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> . Weitere Informationen zum Filtern und Hinzufügen von Elementen zum Dialogfeld **Neues Element hinzu** fügen finden Sie unter [Hinzufügen von Elementen zu den Dialogfeldern Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)
