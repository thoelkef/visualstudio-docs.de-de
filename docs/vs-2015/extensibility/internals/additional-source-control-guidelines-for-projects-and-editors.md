---
title: Richtlinien für die zusätzliche Quellcodeverwaltung für Projekte und Editoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b671397e5be6701176fc0fd5aaa3ae2be24e609
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515630"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Zusätzliche Richtlinien für die Quellcodeverwaltung für Projekte und Editoren
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [zusätzliche Richtlinien für die Quellcodeverwaltung für Projekte und Editoren](https://docs.microsoft.com/visualstudio/extensibility/internals/additional-source-control-guidelines-for-projects-and-editors).  
  
Es gibt eine Anzahl von Richtlinien, denen Projekte und Editoren die entsprechen sollte, um Datenquellen-Steuerelement zu unterstützen.  
  
## <a name="guidelines"></a>Richtlinien  
 Ihrem Projekt oder Editor tun Folgendes ein, um die Datenquellen-Steuerelement unterstützt auch:  
  
|Bereich|Projekt|Editor|Details|  
|----------|-------------|------------|-------------|  
|Private Kopien der Dateien|X||Die Umgebung unterstützt private Kopien der Dateien. Das heißt, hat jede Person, die in das Projekt eingetragen, seine eigene private Kopie der Dateien in diesem Projekt.|  
|ANSI/Unicode-Persistenz|X|X|Wenn Sie den Persistenzcode schreiben, beibehalten von Dateien in die ANSI-Format, da die meisten quellcodeverwaltungsprogrammen Unicode derzeit nicht unterstützt werden.|  
|Auflisten von Dateien|X||Das Projekt muss eine bestimmte Liste aller Dateien darin enthalten und muss in der Lage, das Auflisten von Dateien mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Das Projekt sollte auch verfügbar machen Elementnamen über seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> Implementierung und keinen Support-Lookup von Namen (einschließlich spezielle Dateien) über die <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> Implementierung.|  
|Text-format|X|X|Wenn möglich, sollte die Dateien im Text-Format, um das Zusammenführen von verschiedenen Versionen zu unterstützen. Dateien, die nicht im Text-Format können nicht später mit anderen Versionen der Datei zusammengeführt werden. Die bevorzugten Text-Format ist XML.|  
|Anhand von verweisen|X||Referenz-basierte Projekte werden sofort in der quellcodeverwaltung unterstützt. Verzeichnisbasierte Projekte werden jedoch auch von der quellcodeverwaltung unterstützt, solange eine Liste der Dateien bei Bedarf, unabhängig davon, ob die Dateien auf dem Datenträger vorhanden sind das Projekt erstellt werden kann. Wenn Sie ein Projekt aus der quellcodeverwaltung zu öffnen, wird die Datei zuerst, bevor Sie eine der Dateien geschaltet.|  
|Beibehalten von Objekten und Eigenschaften in einer vorhersagbaren Reihenfolge|X|X|Speichern Sie Ihre Dateien in einer vorhersagbaren Reihenfolge, z. B. alphabetischer Reihenfolge, um die Zusammenführung zu vereinfachen.|  
|Erneut laden|X|X|Wenn eine Datei ändert auf dem Datenträger, muss Ihre-Editor erneut geladen werden. Wenn Sie in der quellcodeverwaltung teilnehmen, die Umgebung werden Daten neu laden für Sie durch den Aufruf Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung. Der schwierigste erneut laden-Fall ist, wenn ein Auschecken tritt auf, wenn Sie IVsQueryEditQuerySave aufgerufen haben::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und Informationen verarbeiten. Allerdings muss Ihren Code erneut laden in diesem Fall führen können.<br /><br /> Die Umgebung lädt automatisch die Projektdateien. Allerdings muss ein Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> sie geschachtelte geschachtelte Hierarchien, um das erneute Laden unterstützen Projektdateien.|  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)

