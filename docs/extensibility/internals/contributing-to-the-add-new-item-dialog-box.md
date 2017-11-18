---
title: "Zu den im Dialogfeld Neues Element hinzufügen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 13f4d254027fe168018fe597f772518bd8ac6b94
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Zu den im Dialogfeld Neues Element hinzufügen
Ein Projektuntertyp bietet ein vollständiges neues Verzeichnis von Elementen für die **neues Element hinzufügen** (Dialogfeld), indem Sie registrieren **Element hinzufügen** Vorlagen unter dem `Projects` Registrierungsunterschlüssel.  
  
## <a name="registering-add-new-item-templates"></a>Registrieren zum Hinzufügen neuer Elemente Vorlagen  
 Dieser Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** in der Registrierung. Die folgenden Registrierungseinträge angenommen ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt wird durch einen hypothetischen Projektuntertyp aggregiert. Die Einträge für die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt sind unten aufgeführt.  
  
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
  
 Die `AddItemTemplates\TemplateDirs` Unterschlüssel enthält Einträge in der Registrierung durch den Pfad zu dem Verzeichnis, in dem Elemente im zur Verfügung gestellt, der **neues Element hinzufügen** Dialogfeld platziert werden.  
  
 Die Umgebung lädt automatisch alle von der `AddItemTemplates` Daten unter der `Projects` Registrierungsunterschlüssel. Dies kann die Daten für Basisprojekt Implementierungen sowie die Daten für bestimmte Untertyp Projekttypen einschließen. Jedes Projektuntertyp wird durch einen Projekttyp identifiziert `GUID`. Untertyp des Projekts kann angeben, dass alternative Satz `Add Item` Vorlagen sollte für einen bestimmten Flavor-Projektsystem Projektinstanz verwendet werden, durch die Unterstützung der `VSHPROPID_ AddItemTemplatesGuid` Enumeration von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> -Implementierung, die die GUID zurück der Wert der Untertyp des Projekts. Wenn `VSHPROPID_AddItemTemplatesGuid` Eigenschaft nicht angegeben wird, das Basisprojekt GUID verwendete.  
  
 Sie können Elemente in Filtern die **neues Element hinzufügen** (Dialogfeld), durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Schnittstelle für das Projekt Untertyp Aggregator-Objekt. Z. B. ein Projektuntertyp, der ein Datenbankprojekt durch aggregieren implementiert eine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt, Filtern können der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] spezifischen Elemente aus der **neues Element hinzufügen** Dialogfeld durch Filterung implementieren, und aktivieren, können hinzufügen Datenbank-Projekt bestimmte Elemente durch die Unterstützung `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Weitere Informationen zu filtern und Hinzufügen von Elementen der **neues Element hinzufügen** (Dialogfeld), finden Sie unter [Elemente hinzufügen, um das Dialogfelder Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)