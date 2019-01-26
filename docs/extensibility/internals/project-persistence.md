---
title: Persistenz Projekt | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15b605d4beffc85c2ac5e8803d627c13dd4c7d38
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55021805"
---
# <a name="project-persistence"></a>Projektpersistenz
Persistenz ist eine wichtige Design-Überlegungen für das Projekt. Die meisten Projekte verwenden Projektelemente, die Dateien darstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt auch Projekte, deren Daten nicht dateibasierte sind. Alle Dateien im Besitz des Projekts und die Projektdatei müssen beibehalten werden. Die IDE weist das Projekt, um sich selbst oder ein Projektelement speichern.  
  
 Vorlagen für Projekte, die auf die Projektzuordnungsinstanz übergeben werden. Die Vorlagen sollten die Initialisierung von alle Projektelemente gemäß den Anforderungen der bestimmten Projekttyp unterstützen. Diese Vorlagen können später als Projektdateien gespeichert und von der IDE über die Lösung verwaltet werden. Weitere Informationen finden Sie unter [erstellen Projekt Instanzen von mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) und [Lösungen](../../extensibility/internals/solutions.md).  
  
 Projektelemente können es sich um einen dateibasierten oder nicht dateibasierte sein:  
  
-   Dateibasierte Elemente können lokal oder remote sein. In Webprojekten in C# geschrieben beibehalten, z. B. Verbindungen mit Dateien auf einem Remotesystem lokal, während die Dateien selbst auf dem remoten System beibehalten werden.  
  
-   Nicht dateibasierte Elemente können Elemente in einer Datenbank oder einem Repository speichern.  
  
## <a name="commit-models"></a>Commit-Modelle  
 Nach der Entscheidung, wo sich die Projektelemente befinden, müssen Sie die entsprechenden Commit-Modell auswählen. Beispielsweise kann in einem dateibasierten Modell mit lokalen Dateien, jedes Projekt autonom gespeichert werden. In einem Repository-Modell können Sie mehrere Elemente in einer Transaktion speichern. Weitere Informationen finden Sie unter [Entwurfsentscheidungen bei Projekttypen](../../extensibility/internals/project-type-design-decisions.md).  
  
 Um Dateinamenerweiterungen Weitere Erweiterungen zu bestimmen, implementieren Sie Projekte der <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> -Schnittstelle, die Informationen den Client zum Implementieren eines Objekts aktivieren die **speichern unter** Dialogfeld –, also Ausfüllen der **speichern als Typ**  Dropdownliste auflisten und verwalten die anfänglichen Erweiterung.  
  
 Die IDE-Aufrufe der `IPersistFileFormat` Schnittstelle für das Projekt aus, um anzugeben, dass das Projekt ein Projekt beibehalten werden soll, Elemente nach Bedarf. Aus diesem Grund besitzt das Objekt alle Aspekte der zugehörigen Dateien und Format. Dies schließt den Namen des Formats des Objekts.  
  
 Im Fall, in denen Elemente keine Dateien sind, `IPersistFileFormat` ist immer noch wie nicht-dateibasierte Elemente beibehalten werden. Dateien, z. B. .vbp-Dateien für Projekt [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] Projekte oder VCPROJ-Dateien für [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] -Projekten muss auch beibehalten werden.  
  
 Für Speichern Aktionen der ausgeführten Dokumententabelle (RDT) die IDE überprüft und die Hierarchie übergibt die Befehle an die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Methode wird implementiert, um zu bestimmen, ob das Element geändert wurde. Wenn das Element verfügt, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> Methode wird implementiert, um das geänderte Element zu speichern.  
  
 Die Methoden für die `IVsPersistHierarchyItem2` Schnittstelle werden verwendet, um zu bestimmen, ob ein Element erneut geladen werden kann, und das Element erneut geladen werden kann,. Darüber hinaus die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> -Methode kann implementiert werden, um die dazu führen, dass bei der geänderte Elementen, die verworfen werden, ohne gespeichert zu werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)   
 [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)