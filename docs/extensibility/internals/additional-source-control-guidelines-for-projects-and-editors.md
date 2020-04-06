---
title: Zusätzliche Quellcodeverwaltungsrichtlinien für Projekte und Editoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], guidelines for projects and editors
ms.assetid: 2483cce5-321c-4d3c-9c5c-ee8385263f74
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 181f6c10ff7ce95cd3a37151f117353d1bb47d41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710106"
---
# <a name="additional-source-control-guidelines-for-projects-and-editors"></a>Zusätzliche Quellcodeverwaltungsrichtlinien für Projekte und Editoren
Es gibt eine Reihe von Richtlinien, die Projekte und Redakteure einhalten sollten, um die Quellcodeverwaltung zu unterstützen.

## <a name="guidelines"></a>Richtlinien
 Ihr Projekt oder Editor sollte auch die folgenden Schritte ausführen, um die Quellcodeverwaltung zu unterstützen:

|Bereich|Project|Editor|Details|
|----------|-------------|------------|-------------|
|Private Kopien von Dateien|X||Die Umgebung unterstützt private Kopien von Dateien. Das heißt, jede Person, die in das Projekt aufgenommen wird, verfügt über eine eigene private Kopie der Dateien in diesem Projekt.|
|ANSI/Unicode-Persistenz|X|X|Wenn Sie den Persistenzcode schreiben, behalten Sie Dateien im ANSI-Formular bei, da die meisten Quellcodeverwaltungsprogramme Unicode derzeit nicht unterstützen.|
|Aufzählen von Dateien|X||Das Projekt muss eine bestimmte Liste aller darin enthaltenen Dateien enthalten und in der <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> Lage sein, die Liste der Dateien aufzulisten, die den oder (VSH_PROPID_First_Child/Next_Sibling) verwenden. Das Projekt sollte elementsnamen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.GetMkDocument%2A> auch durch seine Implementierung verfügbar machen <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject.IsDocumentInProject%2A> und die Namenssuche (einschließlich spezieller Dateien) durch seine Implementierung unterstützen.|
|Textformat|X|X|Wenn möglich, sollten Dateien im Textformat vorliegen, um das Zusammenführen verschiedener Versionen zu unterstützen. Dateien, die nicht im Textformat vorliegen, können später nicht mit anderen Versionen der Datei zusammengeführt werden. Das bevorzugte Textformat ist XML.|
|Referenzbasiert|X||Referenzbasierte Projekte werden in der Quellcodeverwaltung problemlos unterstützt. Verzeichnisbasierte Projekte werden jedoch auch von der Quellcodeverwaltung unterstützt, solange das Projekt eine Liste seiner Dateien bei Bedarf erstellen kann, unabhängig davon, ob diese Dateien auf dem Datenträger vorhanden sind. Wenn Sie ein Projekt aus der Quellcodeverwaltung öffnen, wird die Projektdatei zuerst vor einer ihrer Dateien heruntergefahren.|
|Objekte und Eigenschaften in vorhersagbarer Reihenfolge beibehalten|X|X|Befolgen Sie Ihre Dateien in einer vorhersagbaren Reihenfolge, z. B. in alphabetischer Reihenfolge, um das Zusammenführen zu erleichtern.|
|Erneut laden|X|X|Wenn sich eine Datei auf dem Datenträger ändert, muss der Editor in der Lage sein, sie neu zu laden. Wenn Sie an der Quellcodeverwaltung teilnehmen, lädt die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.ReloadDocData%2A> Umgebung Die Daten für Sie neu, indem Sie Ihre Implementierung aufrufen. Der schwierigste Fall beim erneuten Laden ist, wenn ein Auschecken<xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> auftritt, wenn Sie IVsQueryEditQuerySave:: aufgerufen haben und Informationen verarbeiten. Ihr Neuladecode muss jedoch in dieser Situation ausgeführt werden können.<br /><br /> Die Umgebung lädt Projektdateien automatisch neu. Ein Projekt muss <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2> jedoch implementiert werden, wenn es über verschachtelte Hierarchien verfügt, um das erneute Laden verschachtelter Projektdateien zu unterstützen.|

## <a name="see-also"></a>Weitere Informationen
- [Unterstützung der Quellcodeverwaltung](../../extensibility/internals/supporting-source-control.md)
