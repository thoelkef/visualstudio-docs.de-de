---
title: Persistenz und die Ausführung zu dokumentieren Tabelle | Microsoft-Dokumentation
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
ms.openlocfilehash: d80932ab926b7ef26eaef10991e4f5782e81c4b5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328519"
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die aktive Dokumenttabelle
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE-Projekte sind vollständig verantwortlich für die Verwaltung von Projektelementen, die sie mit dem Dienst zu erreichen, die Persistenz <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumente sind die grundlegende Einheit der Persistenz in Visual Studio-Umgebung. Projekte koordiniert das Öffnen, speichern und Umbenennen von Dokumenten mit der aktiven Dokumenttabelle (RDT), eine Ressource, die den Status aller geöffneten Dokumente nachverfolgt werden.

## <a name="managing-persistence"></a>Verwalten der Persistenz
 Projekte Steuern der Umgebung Persistenzdienst durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Schnittstelle. Während die Umgebung nie direkt ein Dokument selbst beibehalten anfordert, fordert das besitzende Projekt (oder Hierarchie) zum Speichern des Dokuments. Dadurch wird es möglich, dass das Projekt, um die Project-Element-Daten in lokalen Dateien, remote-Dateien, eine Datenbank, ein Repository oder ein anderes Medium zu speichern.

 Die globale Umgebung verwaltet der RDT. Die Umgebung verwaltet Einträge für alle geöffneten Fenster und Dokumente in der RDT, damit sie dadurch erhalten spezielle Benachrichtigungen, z.B. wenn eine Projektmappe geschlossen wird. Darüber hinaus RDT ermöglicht es der Umgebung zum Nachverfolgen der entsprechenden Knoten in **Projektmappen-Explorer**. Der RDT verwaltet einen Datensatz pro öffnen, dauerhafte-Objekt, einschließlich Projektdateien und Projektelement Dokumente.

## <a name="see-also"></a>Siehe auch
- [Aktive Dokumenttabelle](../../extensibility/internals/running-document-table.md)
- [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)