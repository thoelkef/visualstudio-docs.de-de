---
title: Mitwirkung an der im Dialogfeld Neues Element hinzufügen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Add New Item dialog box, contributing to
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 19
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b7e9ce7df2adc05468a27de5f4eaac52c68a07e7
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49215890"
---
# <a name="contributing-to-the-add-new-item-dialog-box"></a>Mitwirken am Dialogfeld „Neues Element hinzufügen“
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Einem Projektuntertyp bieten ein vollständiges neues Verzeichnis von Elementen für die **neues Element hinzufügen** Dialogfeld durch die Registrierung **Element hinzufügen** Vorlagen unter dem `Projects` Unterschlüssel der Registrierung.  
  
## <a name="registering-add-new-item-templates"></a>Registrieren von Vorlagen zum Hinzufügen neuer Elemente  
 In diesem Abschnitt befindet sich unter **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\8.0\Projects** in der Registrierung. Die unten genannten Registrierungseinträge angenommen ein [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt von einem hypothetischen Projektuntertyp aggregiert. Die Einträge für die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Projekt sind unten aufgeführt.  
  
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
  
 Die `AddItemTemplates\TemplateDirs` Unterschlüssel enthält Einträge in der Registrierung durch den Pfad zu dem Verzeichnis, in dem Elemente zur Verfügung gestellt, der **neues Element hinzufügen** Dialogfeld platziert werden.  
  
 Die Umgebung lädt automatisch alle die `AddItemTemplates` Daten unter den `Projects` Unterschlüssel der Registrierung. Dies kann die Daten für Basisprojekt Implementierungen sowie die Daten zu bestimmten Untertyp Projekttypen einschließen. Jede Projektuntertyp wird durch einen Projekttyp identifiziert `GUID`. Der Projektuntertyp kann angeben, dass eine Alternative Gruppe `Add Item` Vorlagen sollten für ein bestimmtes Projekt-Instanz verwendet werden, durch die Unterstützung der `VSHPROPID_ AddItemTemplatesGuid` Enumeration aus <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Implementierung, die die GUID zurück. der Wert des projektuntertyps. Wenn `VSHPROPID_AddItemTemplatesGuid` Eigenschaft nicht angegeben ist, das Basisprojekt GUID wird verwendet.  
  
 Sie können Filtern von Elementen in der **neues Element hinzufügen** Dialogfeld durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg> Schnittstelle für das Projekt Untertyp-Aggregator-Objekt. Z. B. einem Projektuntertyp, die ein Datenbankprojekt durch aggregieren implementiert eine [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] projizieren, Filtern die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] spezifische Elemente aus der **neues Element hinzufügen** Dialogfeld durch die Implementierung von Filtern zu aktivieren, können hinzufügen Datenbank-Projekt bestimmte Elemente durch die Unterstützung von `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>. Weitere Informationen zu filtern und Hinzufügen von Elementen, die **neues Element hinzufügen** im Dialogfeld finden Sie unter [Elemente hinzufügen, um das Hinzufügen neuer Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs für Objekte, die in der Regel zum Erweitern von Projekten verwendet werden](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)

