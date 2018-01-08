---
title: VSTextView Objekt | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: "8"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f169c3302b3e6fd72e5017193e34836ed3e5340e
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="vstextview-object"></a>VSTextView-Objekt
Textansicht ist ein Fenster, können Benutzern das Anzeigen und bearbeiten Sie den Unicode-Text des Textpuffers. Im Wesentlichen wird angezeigt, worauf die meisten Benutzer als Editor verweisen. Da die Sicht aus dem Puffer von verschiedenen Ebenen (Zeilenumbruch, Gliederung Text usw.) getrennt ist, wird die Ansicht nicht unbedingt eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht, finden Sie unter [TheText Ansicht über die Legacy-API zugreifen](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Die folgende Tabelle enthält die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|[IDropSource](http://msdn.microsoft.com/library/windows/desktop/ms690071)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von zusammengesetzten Aktivitäten (Aktivitäten, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert werden).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegende Methoden zum Verwalten von und Zugreifen auf die Ansicht bereit. `IVsTextView`ist nicht threadsicher.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und einen Fensterbereich verwaltet.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagiert mit Textebenen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Sicht aus einem anderen Thread aus.|  
  
## <a name="see-also"></a>Siehe auch  
 [Bearbeiten von Zahlen](http://msdn.microsoft.com/en-us/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)   
 [Zugreifen auf TheText Ansicht über die Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)