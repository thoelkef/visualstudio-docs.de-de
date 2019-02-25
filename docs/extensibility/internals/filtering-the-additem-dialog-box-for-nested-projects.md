---
title: Filtern des AddItem-Dialogfelds für geschachtelte Projekte | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 38b56753bfc56a1143d8c5423ddf7714f0b2f21e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606029"
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