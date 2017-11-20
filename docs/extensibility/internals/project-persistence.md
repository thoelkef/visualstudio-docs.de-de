---
title: Persistenz Projekt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7bb782b79c00576a431c8f4453ddf020606aaf5a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="project-persistence"></a>Projektdauerhaftigkeit
Persistenz ist eine wichtige designüberlegung für das Projekt. Die meisten Projekte verwenden Projektelemente, die Dateien darstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt auch Projekte, deren Daten nicht File-based ist. Beide Dateien im Besitz des Projekts und die Projektdatei müssen beibehalten werden. Die IDE weist das Projekt selbst oder ein Projektelement speichern.  
  
 Vorlagen für Projekte werden mit der Projekt-Factory übergeben. Die Vorlagen sollten die Initialisierung der alle Projektelemente gemäß den Anforderungen der bestimmten Projekttyp unterstützt. Diese Vorlagen können später als die Projektdateien gespeichert und von der IDE über die Lösung verwaltet werden. Weitere Informationen finden Sie unter [erstellen Instanzen von mithilfe von Project Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) und [Lösungen](../../extensibility/internals/solutions.md).  
  
 Projektelemente möglich dateibasierte oder nicht-dateibasierte:  
  
-   Dateibasierte Elemente können lokalen oder Remotecomputer sein. Webprojekte in c# beibehalten werden z. B. Verbindungen mit Dateien auf einem remoten System lokal, während die Dateien selbst auf dem remoten System beibehalten.  
  
-   Nicht-dateibasierte Elemente können Elemente in einer Datenbank oder einem Repository speichern.  
  
## <a name="commit-models"></a>Commit-Modelle  
 Nach der Entscheidung, wo die Projektelemente befinden, müssen Sie die entsprechenden Commit-Modell auswählen. Beispielsweise kann in einem Modell dateibasierte mit lokalen Dateien jedes Projekt autonom gespeichert werden. In einem Repository-Modell können Sie mehrere Elemente in einer Transaktion speichern. Weitere Informationen finden Sie unter [Projekt Typ Entwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).  
  
 Um Dateinamenerweiterungen zu bestimmen, implementieren Sie Projekte die <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> -Schnittstelle, die Informationen ermöglicht dem Client zum Implementieren eines Objekts stellt die **speichern unter** (Dialogfeld) –, also Ausfüllen der **Dateityp**  Dropdownelement auflisten und verwalten Sie die ursprüngliche Dateinamenerweiterung.  
  
 Ruft die IDE die `IPersistFileFormat` Schnittstelle für das Projekt, um anzugeben, dass das Projekt ihr Projekt weiterhin bestehen sollte Elemente nach Bedarf. Aus diesem Grund besitzt das Objekt alle Aspekte der zugehörigen Dateien und Format. Dies schließt den Namen des Formats des Objekts.  
  
 Im Fall, in dem Elemente keine Dateien sind, `IPersistFileFormat` ist immer noch wie nicht-dateibasierte Elemente beibehalten werden. Projektdateien, z. B. vbp-Dateien für [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekte oder .vcproj-Dateien für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] -Projekten auch beibehalten werden muss.  
  
 Für Speichern Aktionen, die ausgeführten Document-Tabelle (RDT) die IDE überprüft und die Hierarchie übergibt die Befehle an, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Methode wird implementiert, um festzustellen, ob das Element geändert wurde. Wenn das Element verfügt, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> Methode wird implementiert, um das geänderte Element zu speichern.  
  
 Die Methoden für die `IVsPersistHierarchyItem2` Schnittstelle werden verwendet, um zu bestimmen, ob ein Element erneut geladen werden kann, und wenn das Element sie erneut geladen werden kann,. Darüber hinaus die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> -Methode kann implementiert werden, um die geänderten Elemente verworfen werden, ohne gespeichert zu werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuen Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)