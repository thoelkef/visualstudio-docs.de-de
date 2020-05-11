---
title: Persistenz und die Tabelle "Laufende Sendedokumente" | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ba698f20b83d1a7af42aeca046aa2a8c943838ef
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706720"
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die aktive Dokumenttabelle
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der IDE sind Projekte vollständig für die Verwaltung der Persistenz ihrer <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>Projektelemente verantwortlich, die sie mit dem Dienst ausführen. Dokumente sind die grundlegende Einheit der Persistenz in der Visual Studio-Umgebung. Projekte koordinieren das Öffnen, Speichern und Umbenennen von Dokumenten mit der laufenden Dokumenttabelle (RDT), einer Ressource, die den Status aller geöffneten Dokumente nachverfolgt.

## <a name="managing-persistence"></a>Verwalten von Persistenz
 Projekte steuern den Persistenzdienst der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Umgebung, indem sie die Schnittstelle implementieren. Während die Umgebung ein Dokument nie direkt dazu auffordert, selbst beizubehalten, fordert sie das besitzende Projekt (oder die Hierarchie) auf, das Dokument zu speichern. Dadurch kann das Projekt seine Projektelementdaten in lokalen Dateien, Remotedateien, einer Datenbank, einem Repository oder einem anderen Medium speichern.

 Die globale Umgebung hält die RDT aufrecht. Die Umgebung verwaltet Einträge für alle geöffneten Fenster und Dokumente im RDT, wodurch sie spezielle Benachrichtigungen erhalten können, z. B. wenn eine Lösung geschlossen wird. Darüber hinaus ermöglicht die RDT der Umgebung, ihre entsprechenden Knoten im **Projektmappen-Explorer**nachzuverfolgen. Der RDT verwaltet einen Datensatz pro geöffnetem, persistenten Objekt, einschließlich Projektdateien und Projektelementdokumenten.

## <a name="see-also"></a>Weitere Informationen
- [Aktive Dokumenttabelle](../../extensibility/internals/running-document-table.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
