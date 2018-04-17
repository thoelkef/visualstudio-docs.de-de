---
title: Richtlinien für zusätzliche Quelle für Projekte und Editoren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e39c8fcc78712f0f8d9b799789751c16f343ada6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Richtlinien für zusätzliche Quelle für Projekte und Editoren
Es gibt diverse Richtlinien, denen Projekte und Editoren folgen soll um Datenquellen-Steuerelements unterstützen.  
  
## <a name="guidelines"></a>Richtlinien  
 Das Projekt oder Editor sollte auch Folgendes ein, um die Datenquellen-Steuerelements unterstützen Aktionen ausführen:  
  
|Bereich|Projekt|Editor|Details|  
|----------|-------------|------------|-------------|  
|Private Kopien von Dateien|X||Die Umgebung unterstützt private Kopien der Dateien. Jede Person, die im Projekt eingetragen wurde, also seine eigenen privaten Kopie der Dateien in diesem Projekt.|  
|ANSI/Unicode-Persistenz|X|X|Wenn Sie die Persistenzcode zu schreiben, beibehalten Sie, Dateien in das ANSI-Format, da die meisten quellcodeverwaltungsprogrammen zurzeit nicht Unicode unterstützen.|  
|Auflisten von Dateien|X||Das Projekt muss eine bestimmte Liste aller Dateien darin enthalten und muss in der Lage, Aufzählen die Liste der Dateien, die mit der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> (VSH_PROPID_First_Child/Next_Sibling). Das Projekt sollte auch verfügbar machen Elementnamen über seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> Implementierung und Unterstützung Namenssuche (einschließlich spezielle Dateien) über seine <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> Implementierung.|  
|Text-format|X|X|Wenn möglich, sollten die Dateien im Text-Format unterstützt das Zusammenführen mit unterschiedlichen Versionen sein. Dateien, die nicht im Text-Format können nicht mit anderen Versionen der Datei später zusammengeführt werden. Die bevorzugten Textformat ist XML.|  
|Anhand von verweisen|X||Verweisbasierten Projekten werden sofort in der quellcodeverwaltung unterstützt. Directory-basierte Projekte werden jedoch auch von Datenquellen-Steuerelement unterstützt, solange das Projekt werden, eine Liste der Dateien bei Bedarf erstellt kann, unabhängig davon, ob diese Dateien auf dem Datenträger vorhanden sind. Wenn Sie ein Projekt aus der quellcodeverwaltung öffnen, wird die Projektdatei zuerst, bevor Sie eine der Dateien geschaltet.|  
|Objekte und Eigenschaften in vorhersagbaren Reihenfolge beibehalten|X|X|Behalten Sie die Dateien in einer vorhersagbaren Reihenfolge, z. B. alphabetischer Reihenfolge an, um das Zusammenführen zu ermöglichen.|  
|zum erneuten Laden|X|X|Wenn eine Datei ändert auf dem Datenträger, muss der Editor können sie erneut geladen. Wenn Sie in der quellcodeverwaltung teilnehmen, laden die Umgebung Daten für Sie durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Implementierung. Die schwierigste Reload Groß-/Kleinschreibung wird beim Auschecken tritt auf, wenn Sie IVsQueryEditQuerySave aufgerufen haben::<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> und Informationen zu Verarbeitungsfehlern sind. Zum erneuten Laden Code muss in dieser Situation ausführen.<br /><br /> Die Umgebung lädt automatisch die Projektdateien. Allerdings muss ein Projekt implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> sie geschachtelte geschachtelte Hierarchien, um erneuten Laden zu unterstützen Projektdateien.|  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützen der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)