---
title: Projekt Persistenz | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, projects
- projects [Visual Studio SDK], persistance
ms.assetid: 42907bcf-4e27-46bd-a8cb-01c2ccd2bde5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 10a9cde91c0181fbfefbaa353c7c3702f4b36819
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706460"
---
# <a name="project-persistence"></a>Projektpersistenz
Persistenz ist eine wichtige Entwurfsüberlegung für Ihr Projekt. Die meisten Projekte verwenden Projektelemente, die Dateien darstellen. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] unterstützt auch Projekte, deren Daten nicht dateibasiert sind. Sowohl die Dateien, die dem Projekt gehören, als auch die Projektdatei müssen beibehalten werden. Die IDE weist das Projekt an, sich selbst oder ein Projektelement zu speichern.

 Vorlagen für Projekte werden an die Projektfactory übergeben. Die Vorlagen sollten die Initialisierung aller Projektelemente entsprechend den Anforderungen des jeweiligen Projekttyps unterstützen. Diese Vorlagen können später als Projektdateien gespeichert und von der IDE über die Projektmappe verwaltet werden. Weitere Informationen finden Sie unter [Erstellen von Projektinstanzen mithilfe von Projektfabriken](../../extensibility/internals/creating-project-instances-by-using-project-factories.md) und [-lösungen](../../extensibility/internals/solutions-overview.md).

 Projektelemente können dateibasiert oder nicht dateibasiert sein:

- Dateibasierte Elemente können lokal oder remote sein. In Webprojekten in C-Dateien bleiben z. B. Verbindungen zu Dateien auf einem Remotesystem lokal bestehen, während die Dateien selbst auf dem Remotesystem verbleiben.

- Nicht dateibasierte Elemente können Elemente in einer Datenbank oder einem Repository speichern.

## <a name="commit-models"></a>Commit-Modelle
 Nachdem Sie entschieden haben, wo sich die Projektelemente befinden, müssen Sie das entsprechende Commitmodell auswählen. In einem dateibasierten Modell mit lokalen Dateien kann z. B. jedes Projekt autonom gespeichert werden. In einem Repository-Modell können Sie mehrere Elemente in einer Transaktion speichern. Weitere Informationen finden Sie unter [Projekttypentwurfsentscheidungen](../../extensibility/internals/project-type-design-decisions.md).

 Um Dateinamenerweiterungen zu <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat> bestimmen, implementieren Projekte die Schnittstelle, die Informationen bereitstellt, die es dem Client eines Objekts ermöglichen, das Dialogfeld **Speichern** unter zu implementieren, d. h. die Dropdownliste **Speichern als Typ** auszufüllen und die ursprüngliche Dateinamenerweiterung zu verwalten.

 Die IDE `IPersistFileFormat` ruft die Schnittstelle im Projekt auf, um anzugeben, dass das Projekt seine Projektelemente entsprechend beibehalten soll. Daher besitzt das Objekt alle Aspekte seiner Datei und seines Formats. Dazu gehört auch der Name des Formats des Objekts.

 In dem Fall, in `IPersistFileFormat` dem Elemente keine Dateien sind, wird immer noch nicht dateibasierte Elemente beibehalten. Projektdateien, z. B. [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] vbp-Dateien für Projekte [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] oder .vcproj-Dateien für Projekte, müssen ebenfalls beibehalten werden.

 Für Speicheraktionen untersucht die IDE die laufende Dokumenttabelle (RDT), und <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> Hierarchie übergibt die Befehle an die und die Schnittstellen. Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.IsItemDirty%2A> Methode wird implementiert, um zu bestimmen, ob das Element geändert wurde. Wenn das Element <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem.SaveItem%2A> hat, wird die Methode implementiert, um das geänderte Element zu speichern.

 Die Methoden `IVsPersistHierarchyItem2` auf der Schnittstelle werden verwendet, um zu bestimmen, ob ein Element neu geladen werden kann, und, falls es das Element sein kann, um es neu zu laden. Darüber hinaus <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IgnoreItemFileChanges%2A> kann die Methode implementiert werden, um zu bewirken, dass geänderte Elemente verworfen werden, ohne gespeichert zu werden.

## <a name="see-also"></a>Weitere Informationen
- [Prüfliste: Erstellen neuer Projekttypen](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Erstellen von Projektinstanzen mithilfe von Projektfactorys](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
