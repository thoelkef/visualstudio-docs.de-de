---
title: Filtern des AddItem-Dialog Felds für in der Liste von Projekten | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708385"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>Dialogfeld "AddItem" für die Liste der Projekte filtern
Wenn Sie ein **AddItem** -Dialogfeld für ein untergeordnetes Projekt anzeigen, kann das übergeordnete Projekt steuern, welche Elemente im Dialogfeld angezeigt werden.

 Mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle können Sie die Knoten filtern, die sich in einem **AddItem** -Dialogfeld befinden. Wenn das untergeordnete Projekt das **AddItem** -Dialogfeld anzeigt, kann das übergeordnete Projekt die `IVsFilterAddProjectItemDlg` -Schnittstelle implementieren und Elemente filtern, die andernfalls im Projekt des Kindes angezeigt werden.

 Wenn Projekte unter bestimmten übergeordneten Projekten nach Funktion gruppiert werden, können Sie implementieren, `IVsFilterAddProjectItemDlg` Wenn der Benutzer im Kontextmenü eines untergeordneten Projekts die Option **Projekt Element hinzufügen** auswählt. `IvsFilterAddProjectItemDlg displays`Nur für diese Gruppe spezifische Projekt Elemente oder Dateien werden implementiert. Projekt Elemente für andere Gruppen werden aus dem Dialogfeld herausgefiltert, auch wenn Sie im selben Verzeichnis gespeichert werden.

 Wenn ein Benutzer das **AddItem** -Dialogfeld für das untergeordnete Element öffnet, wird die Implementierung der-Schnittstelle des übergeordneten Projekts `IVsFilterAddProjectItemDlg` aufgerufen.

 Die `IVsFilterAddProjectItemDlg` Schnittstelle kann auch das Filtern nach Kategorie implementieren. Weitere Informationen finden Sie unter [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) " und [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [Hinzufügen von Elementen zum Dialogfeld "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)
- [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
