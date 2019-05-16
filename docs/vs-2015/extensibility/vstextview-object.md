---
title: VSTextView-Objekt | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSTextView
helpviewer_keywords:
- VSTextView object, reference
- views [Visual Studio SDK], reference
ms.assetid: 78272ddc-9718-4c65-a94e-a44a2e8d54f4
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22e4d4cdf1e5ca610dbdb067f8195fb730139c3d
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65690696"
---
# <a name="vstextview-object"></a>VSTextView-Objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Textansicht ist ein Fenster, können Benutzern das Anzeigen und bearbeiten Sie den Unicode-Text des Textpuffers. Im Wesentlichen ist die Ansicht, was die meisten Benutzer als Editor bezeichnet. Da die Ansicht aus dem Puffer von verschiedenen Textebenen (Zeilenumbruch, Gliederung, Text usw.) getrennt ist, wird die Sicht nicht garantiert eine genaue Darstellung des Texts im Puffer. Weitere Informationen zu der Textansicht, finden Sie unter [TheText Ansicht zugreifen, mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)  
  
 Die folgende Tabelle zeigt die Schnittstellen der <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt.  
  
|Interface|Beschreibung|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von verbundaktionen (d. h. Aktionen, die in einer einzelnen Rückgängig-/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegende Methoden für die Verwaltung und den Zugriff auf die Ansicht bereit. `IVsTextView` ist nicht threadsicher.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interaktion mit Textebenen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Sicht von einem anderen Thread.|  
  
## <a name="see-also"></a>Siehe auch  
 [Abbildungen bearbeiten](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [VSTextBuffer-Objekt](../extensibility/vstextbuffer-object.md)   
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
