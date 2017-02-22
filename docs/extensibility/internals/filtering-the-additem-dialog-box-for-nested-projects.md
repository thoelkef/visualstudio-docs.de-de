---
title: "Das Dialogfeld AddItem Filtern f&#252;r geschachtelte Projekte | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Filtern von geschachtelten Projekte"
  - "geschachtelte Projekten AddItem Dialogfeld Feld filtern"
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Das Dialogfeld AddItem Filtern f&#252;r geschachtelte Projekte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Wenn Sie ein **AddItem** Dialogfeld für ein geschachteltes Projekt anzeigen, kann das übergeordnete Projekt steuern, welche Elemente im Dialogfeld angezeigt werden.  
  
 Die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>\-Schnittstelle können Sie die Knoten filtern, die in einem **AddItem** Dialogfeld sind.  Wenn das untergeordnete Projekt das **AddItem** Dialogfeld anzeigt, kann das übergeordnete Element der `IVsFilterAddProjectItemDlg`\-Schnittstelle implementieren und Elemente filtern, die andernfalls in Projekt des untergeordneten Elements angezeigt werden.  
  
 Wenn Projekte nach Funktion bestimmte Elemente in Projekten gruppiert werden, können Sie `IVsFilterAddProjectItemDlg` implementiert werden, wenn der Benutzer im Kontextmenü **Projektelemente hinzufügen** in einem geschachtelten Projekt ausgewählt werden.  Projektelemente oder Dateien nur `IvsFilterAddProjectItemDlg displays` Implementieren dieser Gruppe bestimmt.  Projektelemente für andere Gruppen werden aus dem Dialogfeld herausgefiltert, auch wenn sie im gleichen Verzeichnis gespeichert sind.  
  
 Wenn ein Benutzer das Dialogfeld **AddItem** für das untergeordnete Element geöffnet wird, wird die übergeordnete Implementierung des Projekts der `IVsFilterAddProjectItemDlg`\-Schnittstelle aufgerufen.  
  
 Die `IVsFilterAddProjectItemDlg`\-Schnittstelle kann das Filtern nach Kategorie ebenfalls implementieren.  Weitere Informationen finden Sie unter [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) und [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Hinzufügen von Elementen, die zum Hinzufügen neuer Elemente Dialogfelder](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt\- und Elementvorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Die Schachtelung von Projekten](../../extensibility/internals/nesting-projects.md)