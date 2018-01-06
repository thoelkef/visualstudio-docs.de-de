---
title: "Persistenz und Ausführung dokumentieren Tabelle | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7f48a1acdad3856e7334ce6a86b48e67c880f9c1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die Ausführung Document-Tabelle
In der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE Projekte werden vollständig verantwortlich für die Verwaltung von Persistenz in ihre Projektelemente, die sie mit dem Dienst zu erreichen, <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable>. Dokumente sind die grundlegende Einheit der Persistenz in der Visual Studio-Umgebung. Projekte koordiniert das Öffnen, speichern und Umbenennen von Dokumenten mit der ausgeführten Dokumenttabelle (RDT), eine Ressource, die den Status aller geöffneten Dokumente nachverfolgt werden.  
  
## <a name="managing-persistence"></a>Verwalten von Persistenz  
 Projekte Steuern der Umgebung Persistenzdienst durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Schnittstelle. Während die Umgebung nie direkt ein Dokument selbst persistent anfordert, fordert er das besitzende Projekt (oder Hierarchie) zum Speichern des Dokuments. Dies ermöglicht es für das Projekt in der Projekt-Elementdaten in lokalen Dateien, remote-Dateien, eine Datenbank, einem Repository oder ein anderes Medium zu speichern.  
  
 Die globale Umgebung verwaltet die RDT. Die Umgebung verwaltet Einträge für alle geöffneten Fenster und Dokumente in der RDT, die es Ihnen ermöglicht, erhalten spezielle Benachrichtigungen, z. B. wenn eine Projektmappe geschlossen wird. Darüber hinaus die RDT ermöglicht es der Umgebung zum Nachverfolgen der entsprechenden Knoten in **Projektmappen-Explorer**. Die RDT verwaltet einen Datensatz pro Objekt definiert geöffnet ist, beibehalten werden kann, einschließlich der Projektdateien und Projektelement Dokumente.  
  
## <a name="see-also"></a>Siehe auch  
 [Dokumenttabelle der ausgeführten](../../extensibility/internals/running-document-table.md)   
 [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)