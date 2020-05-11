---
title: Filtern des AddItem-Dialogfelds für verschachtelte Projekte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708385"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Filtern des Dialogfelds AddItem nach verschachtelten Projekten
Wenn Sie ein **AddItem-Dialogfeld** für ein verschachteltes Projekt anzeigen, kann das übergeordnete Projekt steuern, welche Elemente im Dialogfeld angezeigt werden.

 Mit <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> der Schnittstelle können Sie die Knoten filtern, die sich in einem **AddItem-Dialogfeld** begeben. Wenn das untergeordnete Projekt das **Dialogfeld AddItem** `IVsFilterAddProjectItemDlg` anzeigt, kann das übergeordnete Element die Schnittstelle implementieren und Elemente filtern, die andernfalls im Projekt des untergeordneten Elements angezeigt würden.

 Wenn Projekte nach Funktion unter bestimmten übergeordneten `IVsFilterAddProjectItemDlg` Projekten gruppiert werden, können Sie implementieren, wenn der Benutzer **Projektelement** im Kontextmenü in einem verschachtelten Projekt hinzufügen auswählt. Nur `IvsFilterAddProjectItemDlg displays` Projektelemente oder Dateien, die für diese Gruppe spezifisch sind, werden implementiert. Projektelemente für andere Gruppen werden aus dem Dialogfeld herausgefiltert, auch wenn sie im selben Verzeichnis gespeichert sind.

 Wenn ein Benutzer das **AddItem-Dialogfeld** für das untergeordnete Element `IVsFilterAddProjectItemDlg` öffnet, wird die Implementierung der Schnittstelle durch das übergeordnete Projekt aufgerufen.

 Die `IVsFilterAddProjectItemDlg` Schnittstelle kann auch die Filterung nach Kategorie implementieren. Weitere Informationen finden Sie unter [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) und [Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)registrieren .

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Hinzufügen von Elementen zum Dialogfeld Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Nest-Projekte](../../extensibility/internals/nesting-projects.md)
