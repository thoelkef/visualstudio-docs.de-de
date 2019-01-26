---
title: Mitwirkung an der im Dialogfeld Neues Element hinzufügen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39d88d9e8f5886c74f0c0059066ad240ed725742
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "54938483"
---
# <a name="contribute-to-the-add-new-item-dialog-box"></a>Mitwirken Sie an das Dialogfeld "Neues Element hinzufügen"
Einem Projektuntertyp bieten ein vollständiges neues Verzeichnis von Elementen für die **neues Element hinzufügen** Dialogfeld durch die Registrierung **Element hinzufügen** Vorlagen unter dem **Projekte** Unterschlüssel der Registrierung.  
  
## <a name="register-add-new-item-templates"></a>Neues Element hinzufügen-Vorlagen zu registrieren  
 In diesem Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** in der Registrierung. Die unten genannten Registrierungseinträge angenommen ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt von einem hypothetischen Projektuntertyp aggregiert. Die Einträge für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt sind unten aufgeführt.  
  
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
  
 Die **AddItemTemplates\TemplateDirs** Unterschlüssel enthält Einträge in der Registrierung durch den Pfad zu dem Verzeichnis, in dem Elemente zur Verfügung gestellt, der **neues Element hinzufügen** Dialogfeld platziert werden.  
  
 Die Umgebung lädt automatisch alle die **AddItemTemplates** Daten unter den **Projekte** Unterschlüssel der Registrierung. Diese Daten können die Daten für Basisprojekt Implementierungen sowie die Daten zu bestimmten Untertyp Projekttypen enthalten. Jede Projektuntertyp wird durch einen Projekttyp identifiziert **GUID**. Der Projektuntertyp kann angeben, dass eine Alternative Gruppe **Element hinzufügen** Vorlagen sollten für ein bestimmtes Projekt-Instanz verwendet werden, durch die Unterstützung der `VSHPROPID_ AddItemTemplatesGuid` Enumeration aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> die Implementierung den GUID-Wert des projektuntertyps zurückgegeben. Wenn die `VSHPROPID_AddItemTemplatesGuid` Eigenschaft nicht angegeben ist, das Basisprojekt GUID wird verwendet.  
  
 Sie können Filtern von Elementen in der **neues Element hinzufügen** Dialogfeld durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Schnittstelle für das Projekt Untertyp-Aggregator-Objekt. Z. B. einem Projektuntertyp, die ein Datenbankprojekt durch aggregieren implementiert eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] projizieren, Filtern die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spezifische Elemente aus der **neues Element hinzufügen** Dialogfeld durch die Implementierung von Filtern zu aktivieren, können hinzufügen Datenbank-Projekt-spezifische Elemente durch die Unterstützung von `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Weitere Informationen zu filtern und Hinzufügen von Elementen, die **neues Element hinzufügen** im Dialogfeld finden Sie unter [Elemente hinzufügen, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)