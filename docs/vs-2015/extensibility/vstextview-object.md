---
title: Vstextview-Objekt | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690696"
---
# <a name="vstextview-object"></a>VSTextView-Objekt
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Textansicht ist ein Fenster, in dem Benutzer den Unicode-Text des Text Puffers anzeigen und bearbeiten können. Im Wesentlichen ist die Sicht, auf die die meisten Benutzer als Editor verweisen. Da die Ansicht durch verschiedene Textebenen (Zeilenumbruch, Gliederung von Text usw.) vom Puffer getrennt ist, ist die Sicht nicht garantiert eine exakte Darstellung des Texts im Puffer. Weitere Informationen zur Textansicht finden Sie unter Zugreifen auf die [Textansicht mithilfe der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md) .  
  
 In der folgenden Tabelle werden die Schnittstellen im- <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextView> Objekt angezeigt.  
  
|Schnittstelle|BESCHREIBUNG|  
|---------------|-----------------|  
|[IDropSource](/windows/desktop/api/oleidl/nn-oleidl-idropsource)|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IDropTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IObjectWithSite>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Standard-OLE-Schnittstelle.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompoundAction>|Ermöglicht die Erstellung von Verbund Aktionen (d. h. Aktionen, die in einer einzelnen Rückgängig/Wiederholen-Einheit gruppiert sind).|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView>|Stellt die grundlegenden Methoden zum Verwalten von und Zugreifen auf die Ansicht bereit. `IVsTextView` ist nicht threadsicher.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane>|Erstellt und verwaltet einen Fensterbereich.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView>|Interagiert mit Textebenen.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsThreadSafeTextView>|Führt Vorgänge für die Ansicht aus einem anderen Thread aus.|  
  
## <a name="see-also"></a>Weitere Informationen  
 [Abbildungen bearbeiten](https://msdn.microsoft.com/f08872bd-fd9c-4e36-8cf2-a2a2622ef986)   
 [Vstextbuffer-Objekt](../extensibility/vstextbuffer-object.md)   
 [Zugriff auf die Textansicht mit der Legacy-API](../extensibility/accessing-thetext-view-by-using-the-legacy-api.md)
