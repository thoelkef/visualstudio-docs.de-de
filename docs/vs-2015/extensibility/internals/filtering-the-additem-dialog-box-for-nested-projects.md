---
title: Filtern des AddItem-Dialog Felds für in der Liste von Projekten | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7bb98eac2bc481aa5e3652144dfbcadf70430d04
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538095"
---
# <a name="filtering-the-additem-dialog-box-for-nested-projects"></a>Filtern des AddItem-Dialogfelds für geschachtelte Projekte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Wenn Sie ein **AddItem** -Dialogfeld für ein untergeordnetes Projekt anzeigen, kann das übergeordnete Projekt steuern, welche Elemente im Dialogfeld angezeigt werden.  
  
 Mithilfe der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> Schnittstelle können Sie die Knoten filtern, die sich in einem **AddItem** -Dialogfeld befinden. Wenn das untergeordnete Projekt das **AddItem** -Dialogfeld anzeigt, kann das übergeordnete Projekt die `IVsFilterAddProjectItemDlg` -Schnittstelle implementieren und Elemente filtern, die andernfalls im Projekt des Kindes angezeigt werden.  
  
 Wenn Projekte unter bestimmten übergeordneten Projekten nach Funktion gruppiert werden, können Sie implementieren, `IVsFilterAddProjectItemDlg` Wenn der Benutzer im Kontextmenü eines untergeordneten Projekts die Option **Projekt Element hinzufügen** auswählt. `IvsFilterAddProjectItemDlg displays`Nur für diese Gruppe spezifische Projekt Elemente oder Dateien werden implementiert. Projekt Elemente für andere Gruppen werden aus dem Dialogfeld herausgefiltert, auch wenn Sie im selben Verzeichnis gespeichert werden.  
  
 Wenn ein Benutzer das **AddItem** -Dialogfeld für das untergeordnete Element öffnet, wird die Implementierung der-Schnittstelle des übergeordneten Projekts `IVsFilterAddProjectItemDlg` aufgerufen.  
  
 Die `IVsFilterAddProjectItemDlg` Schnittstelle kann auch das Filtern nach Kategorie implementieren. Weitere Informationen finden Sie unter [Hinzufügen von Elementen zu den Dialog Feldern Neues Element hinzufügen](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) und [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>   
 [Hinzufügen von Elementen zu den Dialog Feldern "Neues Element hinzufügen"](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)   
 [Registrieren von Projekt-und Element Vorlagen](../../extensibility/internals/registering-project-and-item-templates.md)   
 [Schachteln von Projekten](../../extensibility/internals/nesting-projects.md)
