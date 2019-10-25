---
title: Persistenz und die laufende Dokument Tabelle | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f03836e1faaac03fbd89c0b93f37a698cbdcd56a
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726081"
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die aktive Dokumenttabelle
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE sind Projekte vollständig für die Verwaltung der Persistenz ihrer Projekt Elemente verantwortlich, die Sie mit dem Dienst <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> erreichen. Dokumente sind die grundlegende Einheit der Persistenz in der Visual Studio-Umgebung. Projekte koordinieren das Öffnen, speichern und Umbenennen von Dokumenten mit der laufenden dokumententabelle (RDT), einer Ressource, die den Status aller geöffneten Dokumente nachverfolgt.

## <a name="managing-persistence"></a>Verwalten der Persistenz
 Projekte steuern den Persistenzdienst der Umgebung, indem Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem>-Schnittstelle implementieren. Obwohl die Umgebung nicht direkt ein Dokument anfordert, sich selbst beizubehalten, wird das zuständige Projekt (oder die Hierarchie) aufgefordert, das Dokument zu speichern. Dies ermöglicht es dem Projekt, seine Projekt Elementdaten in lokalen Dateien, Remote Dateien, einer Datenbank, einem Repository oder einem anderen Medium zu speichern.

 Die globale Umgebung verwaltet den RDT. In der Umgebung werden Einträge für alle geöffneten Fenster und Dokumente im RDT verwaltet, sodass Sie spezielle Benachrichtigungen erhalten können, z. b. Wenn eine Projekt Mappe geschlossen wird. Außerdem ermöglicht der RDT es der Umgebung, die entsprechenden Knoten in **Projektmappen-Explorer**zu verfolgen. Der RDT verwaltet einen Datensatz pro geöffnetes, dauerhaften Objekt, einschließlich Projektdateien und Projekt Element Dokumenten.

## <a name="see-also"></a>Siehe auch
- [Aktive Dokumenttabelle](../../extensibility/internals/running-document-table.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)