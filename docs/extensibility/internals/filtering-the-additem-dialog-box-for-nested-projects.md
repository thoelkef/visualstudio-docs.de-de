---
title: "Das Dialogfeld AddItem für geschachtelte Projekte filtern | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: e1f5fc7695df028330d0e53faebefc178f499da1
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
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