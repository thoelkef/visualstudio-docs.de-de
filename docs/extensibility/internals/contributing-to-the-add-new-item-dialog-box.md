---
title: "Zu den im Dialogfeld Neues Element hinzuf&#252;gen | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Fügen Sie zu Dialogfeld Neues Element hinzu"
ms.assetid: b2e53175-9372-4d17-8c2b-9264c9e51e9c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Zu den im Dialogfeld Neues Element hinzuf&#252;gen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Ein Projekt untertyp kann ein vollständiges neues Verzeichnis von Elementen für das **Neues Element hinzufügen** Dialogfeld über Registrieren von **Element hinzufügen** Vorlagen unter dem `Projects` Registrierungsunterschlüssel bereitstellen.  
  
## Das Registrieren Sie Neues Element hinzufügen Vorlagen  
 Dieser Abschnitt befindet sich unter **HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\8.0\\Projects** in der Registrierung.  In den nachfolgenden Registrierungseinträge ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt enthalten sind, das durch einen hypothetischen Projekt untertyp aggregiert wird.  Die Einträge für das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekts werden im Folgenden aufgeführt.  
  
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
  
 Der `AddItemTemplates\TemplateDirs` Unterschlüssel enthält die Registrierungseinträge mit dem Pfad des Verzeichnisses ab, in dem die Elemente bereitgestellt **Neues Element hinzufügen** im Dialogfeld platziert werden.  
  
 Die Umgebung wird automatisch alle `AddItemTemplates` Daten mit dem `Projects` Registrierungsunterschlüssel.  Dies kann die Daten für niedrige Projektdurchführungen sowie die Daten für Typen untertyp bestimmtes Projekt einschließen.  Jeder Projektuntertyp wird durch einen Projekttyp `GUID`identifiziert.  Der Projekt untertyp kann angeben, dass eine alternative Gruppe `Add Item` Vorlagen für eine bestimmte Projektinstanz mit dem Typ verwendet werden sollte, indem er die `VSHPROPID_ AddItemTemplatesGuid`\-Enumeration von <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID2> in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Implementierung unterstützt, um den GUID\-Wert des Projekts untertyps zurückzugeben.  Wenn `VSHPROPID_AddItemTemplatesGuid`\-Eigenschaft nicht angegeben ist, wird die Projekt\-GUID verwendet.  
  
 Sie können Elemente im Dialogfeld **Neues Element hinzufügen** filtern, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg>\-Schnittstelle im Projekt untertyp\-Aggregator Objekt implementieren.  Beispielsweise kann ein Projekt untertyp, der ein Datenbankprojekt durchführt, indem ein [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Projekt aggregiert, die einzelnen Elemente im Dialogfeld **Neues Element hinzufügen**[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] filtern, indem er die Filterung implementiert und kann wiederum des Datenbankprojekts indem die Unterstützung von `VSHPROPID_ AddItemTemplatesGuid` in <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A>bestimmte Elemente hinzufügen.  Weitere Informationen zu Filtern und Hinzufügen von Elementen zum **Neues Element hinzufügen** Dialogfeld finden Sie unter [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [CATIDs für Objekte, die in der Regel verwendet werden, um Projekte zu erweitern.](../../extensibility/internals/catids-for-objects-that-are-typically-used-to-extend-projects.md)