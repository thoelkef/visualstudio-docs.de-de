---
title: VSTextView-Objekt | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d5b0b6e640f4fef6cf9508747cff010ff5b5ad6c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495413"
---
# <a name="vstextview-object"></a>VSTextView-Objekt
Die Textansicht ist ein Fenster, das ermöglicht Benutzern das Anzeigen und bearbeiten den Unicode-Text des Textpuffers. Im Wesentlichen ist die Ansicht, was die meisten Benutzer als Editor bezeichnet. Da die Ansicht aus dem Puffer von verschiedenen Textebenen (Zeilenumbruch, Gliederung, Text usw.) getrennt ist, wird die Sicht nicht garantiert eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht, finden Sie unter [zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Die folgende Tabelle zeigt die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von verbundaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegende Methoden für die Verwaltung und den Zugriff auf die Ansicht bereit. `IVsTextView` ist nicht sicher Thread.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interaktion mit Textebenen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Sicht von einem anderen Thread.|  
  
## <a name="see-also"></a>Siehe auch  
 [Abbildungen bearbeiten](https://www.microsoft.com/download/details.aspx?id=55984)   
 [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)   
 [Zugreifen auf TheText Ansicht mit der legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)