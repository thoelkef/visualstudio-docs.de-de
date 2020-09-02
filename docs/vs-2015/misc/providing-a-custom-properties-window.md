---
title: Bereitstellen eines benutzerdefinierten Eigenschaften Fensters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- property browsers, providing
- Properties window, providing your own
ms.assetid: 408dcdef-8ef9-4644-97d2-f311cd35824f
caps.latest.revision: 12
manager: jillfra
ms.openlocfilehash: a244463832ff5620efa74a2c7fd20d6d47d79e76
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62810700"
---
# <a name="providing-a-custom-properties-window"></a>Bereitstellen eines benutzerdefinierten Eigenschaftenfensters
Es ist möglich, für ein bestimmtes Projekt System ein eigenes **Eigenschaften** Fenster bereitzustellen, anstatt das **Eigenschaften** Fenster zu erweitern, das von der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) bereitgestellt wird. Das am häufigsten auftretende Szenario ist, wenn Sie das Objekt, das im Fensterrahmen positioniert ist, selbst implementieren.  
  
 Wenn Sie das Objekt, das im Fensterrahmen nicht positioniert ist, nicht implementieren, aber trotzdem auf andere Weise darauf zugreifen können, gibt es eine Reihe von Möglichkeiten, auf die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> Schnittstelle zuzugreifen, wie im letzten Verfahren auf dieser Seite aufgeführt.  
  
### <a name="to-provide-your-properties-window"></a>So stellen Sie Ihre Eigenschaftenfenster bereit  
  
1. Definieren Sie eine GUID, die die Implementierung des **Eigenschaften** Fensters darstellt.  
  
2. Verwenden Sie in Ihrer <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> Implementierung den- <xref:Microsoft.VisualStudio.Shell.Interop.IProfferService> Dienst, um Ihr **Eigenschaften** Fenster als Dienst für die Visual Studio-Umgebung zu verwenden.  
  
### <a name="to-call-your-properties-window"></a>So greifen Sie auf das Eigenschaften Fenster zu  
  
1. Rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> -Methode auf.  
  
2. `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> aus der, die an <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider> die-Methode geleitet wird <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowPane.SetSite%2A> .  
  
3. <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>Von <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> Dienst abrufen.  
  
4. Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx.OnElementValueChange%2A> mit dem ersten Parameter, der auf festgelegt `SEID_PropertyBrowserSID` ist (aus der- <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> Enumeration entnommen), und dem dritten Parameter, `varValue` , der eine Zeichen folgen Form der GUID darstellt, die das **Eigenschaften** Fenster darstellt. Nehmen Sie diesen Rückruf bei der ersten Erstellung des Dokument Fensters des **Eigenschaften** Fensters nur einmal vor. Nachdem Sie den Befehl aufgerufen haben, wird das Fenster " **Eigenschaften** " mit Ihrem Fensterrahmen verknüpft.  
  
### <a name="to-obtain-the-window-frame-object-when-you-are-not-the-implementer"></a>So rufen Sie das Fensterrahmen Objekt ab, wenn Sie nicht der Implementierer sind  
  
- Sie können `QueryService` für <xref:Microsoft.VisualStudio.Shell.Interop.SVsTrackSelectionEx> den-Dienst von <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.GetProperty%2A> mit dem-Parameter `propid` auf festlegen <xref:Microsoft.VisualStudio.Shell.Interop.__VSFPROPID> .  
  
- Sie können das aktive Dokument Fenster durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> über den SVsMonitorSelection-Dienst abrufen. Legen Sie den Parameter `elementid` auf fest `SEID_WindowFrame` , der aus der- <xref:Microsoft.VisualStudio.VSConstants.VSSELELEMID> Enumeration entnommen wurde.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)   
 [Felder und Schnittstellen des Eigenschaftenfensters](../extensibility/internals/properties-window-fields-and-interfaces.md)