---
title: Speichern eines benutzerdefinierten Dokuments | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- persistence, saving custom documents
- projects [Visual Studio SDK], saving custom documents
- editors [Visual Studio SDK], saving custom documents
ms.assetid: 040b36d6-1f0a-4579-971c-40fbb46ade1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 896d56dc3fd66cd3dd9e733e8ae528ab710dbd83
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56619692"
---
# <a name="saving-a-custom-document"></a>Speichern eines benutzerdefinierten Dokuments
Umgebungshandles der **speichern**, **speichern**, und **Alles speichern** Befehle. Wenn ein Benutzer klickt **speichern**, **speichern**, **oder speichern Sie alle** auf die **Datei** Menü oder schließt die Projektmappe, wodurch alle speichern, die folgenden erfolgt.

 ![Speichern im Kunden-Editor](../../extensibility/internals/media/private.gif "Private") speichern, speichern und alle speichern Klassenbehandlung für einen benutzerdefinierten Editor-Befehl

 Dieser Prozess wird in den folgenden Schritten beschrieben:

1.  Für die **speichern** und **speichern** Befehle, die Umgebung verwendet die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> service, um zu bestimmen, das das aktive Fenster, und somit welche Elemente gespeichert werden soll. Nachdem das aktive Dokumentfenster bekannt ist, sucht die Umgebung für das Dokument in der ausgeführten Dokumententabelle Hierarchie Zeiger und Elementbezeichner (Element-ID). Weitere Informationen finden Sie unter [Running Document Table](../../extensibility/internals/running-document-table.md).

     Für den Befehl Alle speichern verwendet die Umgebung die Informationen in der ausgeführten Dokumententabelle, kompilieren Sie die Liste der zu speichernden alle Elemente.

2.  Wenn die Lösung empfängt eine <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> aufrufen, wird der Satz von ausgewählten Elementen durchlaufen (, also die Mehrfachauswahl von verfügbar gemacht werden die <xref:Microsoft.VisualStudio.Shell.Interop.SVsShellMonitorSelection> Service).

3.  Die Lösung verwendet für jedes Element in der Auswahl den Hierarchie Zeiger aufrufen, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.IsItemDirty%2A> Methode, um zu bestimmen, ob der Kontextmenübefehl von "Speichern" aktiviert werden soll. Wenn ein oder mehrere Elemente geändert werden, ist der Befehl "Speichern" aktiviert. Wenn die Hierarchie ein standard-Editors verwendet wird, klicken Sie dann die Hierarchie-Delegaten, die für Abfragen dirty-Status in den Editor durch Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistDocData2.IsDocDataDirty%2A> Methode.

4.  Für jedes ausgewählte Element, das geändert wurde, verwendet die Lösung den Hierarchie Zeiger zum Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPersistHierarchyItem2.SaveItem%2A> Methode auf die entsprechenden Hierarchien.

     Bei einem benutzerdefinierten Editor ist die Kommunikation zwischen das dokumentendatenobjekt und das Projekt privat. Daher werden speziellen persistenzaspekte zwischen diesen beiden Objekten behandelt.

    > [!NOTE]
    >  Wenn Sie Ihre eigenen Persistenz implementieren, müssen Sie unbedingt Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> Methode, um Zeit zu sparen. Diese Methode überprüft, um sicherzustellen, dass sie zum Speichern der Datei sicher ist (z. B. die Datei ist nicht schreibgeschützt).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [Öffnen und Speichern von Projektelementen](../../extensibility/internals/opening-and-saving-project-items.md)