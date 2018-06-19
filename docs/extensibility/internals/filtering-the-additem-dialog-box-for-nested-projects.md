---
title: Das Dialogfeld AddItem für geschachtelte Projekte filtern | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 50a9491dad92e4f1dd090a6de1ebf48ef1b88085
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31128857"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Das Dialogfeld AddItem Filtern für geschachtelte Projekte
Beim Anzeigen einer **AddItem** im Dialogfeld für einen geschachtelten Projekts, das übergeordnete Projekt kann steuern, welche Elemente Sie im Dialogfeld angezeigt werden.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle können Sie die Knoten zu filtern, die in einer **AddItem** (Dialogfeld). Wenn das untergeordnete Projekt zeigt die **AddItem** kann implementieren, klicken Sie im Dialogfeld das übergeordnete Element der `IVsFilterAddProjectItemDlg` Schnittstelle und Filter-Elemente, die andernfalls im das untergeordnete Projekt angezeigt werden soll.  
  
 Wenn Projekte nach ihrer Funktion unter bestimmten übergeordneten Projekte gruppiert sind, implementieren Sie `IVsFilterAddProjectItemDlg` Wenn der Benutzer wählt **Projektelement hinzufügen** im Kontextmenü in einer geschachtelten Projekts. Implementieren von `IvsFilterAddProjectItemDlg displays` nur Projekt Elemente oder Dateien für diese Gruppe spezifisch. Projektelemente für andere Gruppen sind aus das Dialogfeld herausgefiltert, auch wenn sie im gleichen Verzeichnis gespeichert werden.  
  
 Wenn ein Benutzer öffnet die **AddItem** im Dialogfeld für das untergeordnete Element des übergeordneten Projekts Implementierung von der `IVsFilterAddProjectItemDlg` -Schnittstelle aufgerufen wird.  
  
 Die `IVsFilterAddProjectItemDlg` Schnittstelle kann auch implementieren nach Kategorie filtern. Weitere Informationen finden Sie unter [Elemente hinzufügen, um das Dialogfelder Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) und [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)