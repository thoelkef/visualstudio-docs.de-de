---
title: Filtern des AddItem-Dialogfelds für geschachtelte Projekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bc3ff1f85e8c8c71bf8ef16e6fe0c89bf3613f4d
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66328947"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtern Sie im Dialogfeld "AddItem" für geschachtelte Projekte
Beim Anzeigen einer **AddItem** eines geschachtelten Projekts, das übergeordnete Projekt im Dialogfeld kann steuern, welche Elemente im Dialogfeld angezeigt werden.

 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle können Sie die Knoten zu filtern, die in einer **AddItem** Dialogfeld. Wenn das untergeordnete Projekt angezeigt wird, die **AddItem** kann implementieren, klicken Sie im Dialogfeld das übergeordnete Element der `IVsFilterAddProjectItemDlg` -Schnittstelle und Filtern von Elementen, die andernfalls in des untergeordneten Standortes Projekt angezeigt werden.

 Wenn Sie Projekte nach ihrer Funktion unter bestimmten übergeordneten Projekte gruppiert sind, können Sie implementieren `IVsFilterAddProjectItemDlg` Wenn der Benutzer auswählt **Projektelemente hinzufügen** im Kontextmenü in einem geschachtelten Projekt. Implementieren von `IvsFilterAddProjectItemDlg displays` nur Projekt Elemente oder speziell für diese Gruppe von Dateien. Projektelemente für andere Gruppen werden aus dem Dialogfeld gefiltert, auch wenn sie im gleichen Verzeichnis gespeichert werden.

 Wenn ein Benutzer öffnet die **AddItem** im Dialogfeld für das untergeordnete Element des übergeordneten Projekts Implementierung der `IVsFilterAddProjectItemDlg` Schnittstelle aufgerufen wird.

 Die `IVsFilterAddProjectItemDlg` Schnittstelle können Sie auch implementieren nach Kategorie filtern. Weitere Informationen finden Sie unter [Elemente hinzufügen, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Fügen Sie Elemente hinzu, um das Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)