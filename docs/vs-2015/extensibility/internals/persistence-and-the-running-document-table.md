---
title: Persistenz und die laufende Dokument Tabelle | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- persistence, managing
- IVsPersistHierarchyItem interface, implementing
- architecture, persistence
- running document table (RDT), architecture
ms.assetid: 27117eae-6c58-4189-a61a-1397a43b5ecf
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2c422ad1735312c82c8dc027c4adf73c1b033685
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196093"
---
# <a name="persistence-and-the-running-document-table"></a>Persistenz und die aktive Dokumenttabelle
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE sind Projekte vollständig für die Verwaltung der Persistenz ihrer Projekt Elemente verantwortlich, die Sie mit dem Dienst erreichen <xref:Microsoft.VisualStudio.Shell.Interop.SVsRunningDocumentTable> . Dokumente sind die grundlegende Einheit der Persistenz in der Visual Studio-Umgebung. Projekte koordinieren das Öffnen, speichern und Umbenennen von Dokumenten mit der laufenden dokumententabelle (RDT), einer Ressource, die den Status aller geöffneten Dokumente nachverfolgt.  
  
## <a name="managing-persistence"></a>Verwalten der Persistenz  
 Projekte steuern den Persistenzdienst der Umgebung durch Implementieren der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem> Schnittstelle. Obwohl die Umgebung nicht direkt ein Dokument anfordert, sich selbst beizubehalten, wird das zuständige Projekt (oder die Hierarchie) aufgefordert, das Dokument zu speichern. Dies ermöglicht es dem Projekt, seine Projekt Elementdaten in lokalen Dateien, Remote Dateien, einer Datenbank, einem Repository oder einem anderen Medium zu speichern.  
  
 Die globale Umgebung verwaltet den RDT. In der Umgebung werden Einträge für alle geöffneten Fenster und Dokumente im RDT verwaltet, sodass Sie spezielle Benachrichtigungen erhalten können, z. b. Wenn eine Projekt Mappe geschlossen wird. Außerdem ermöglicht der RDT es der Umgebung, die entsprechenden Knoten in **Projektmappen-Explorer**zu verfolgen. Der RDT verwaltet einen Datensatz pro geöffnetes, dauerhaften Objekt, einschließlich Projektdateien und Projekt Element Dokumenten.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Ausführen der dokumententabelle](../../extensibility/internals/running-document-table.md)   
 [Auswahl und Aktualität in der IDE](../../extensibility/internals/selection-and-currency-in-the-ide.md)
