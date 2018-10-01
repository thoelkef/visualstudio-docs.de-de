---
title: Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: douge
ms.openlocfilehash: 0272ba348e29fb1a2a118a0ff4b0989a2aa1683f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47513504"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Die erste besteht darin, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> Schnittstelle, die Zugriff auf grundlegende Fensterfunktionalität, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenster-Fenstern, die von der Umgebung bereitgestellten bereitstellt. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Dienst) jedes Mal, wenn VSPackages, Projekte oder Editoren erstellen oder Tool-oder Dokumentfenster durchlaufen müssen.  
  
2.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zu der **Eigenschaften** Fensters mit eigenschaftsänderungen für ein Projekt (oder ein anderes Objekt durchsucht werden, indem die **Eigenschaften** Fenster) ohne die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und das Auslösen von <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> Ereignisse.  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> um einzurichten und zu deaktivieren, bzw. die Clientbenachrichtigung von hierarchieereignissen, ohne dass der Hierarchie implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection  
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor>. Die <xref:System.ComponentModel.ICustomTypeDescriptor> Implementierung kann ändern, die von ihr zurückgegebenen Eigenschaftsdeskriptoren und ändern Sie den Namen einer Eigenschaft. Um die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das abgeleitet <xref:System.ComponentModel.DescriptionAttribute> und überschreiben Sie die Description-Eigenschaft.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle  
  
1.  `IConnection` ermöglicht den Zugriff auf ein enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle. Es bietet außerdem Zugriff auf alle die verbindungspunktunterobjekte, aller implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle.  
  
2.  Jedes ist verantwortlich für die Implementierung einer <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> Ereignis. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.  
  
3.  Ein Verbindungspunkt steuert, wie viele Verbindungen (ein oder mehrere) ermöglicht es in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Ein Verbindungspunkt, der nur eine Schnittstelle ermöglicht zurückgeben kann <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> Methode.  
  
4.  Ein Client aufrufen kann die `IConnection` Schnittstelle, um den Zugriff auf ein enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) aufgelistet werden.  
  
5.  `IConnection` kann auch aufgerufen werden, für den Zugriff auf verbindungspunktunterobjekte mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für jede ausgehende IID. Durch die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> -Schnittstelle, ein Client startet oder beendet eine Beratende Schleife mit dem verbindungsfähigen Objekt und die Synchronisierung des Clients. Der Client kann auch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle zum Abrufen von ein Enumeratorobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> Schnittstelle, um die Verbindungen aufzulisten, die sie bekannt sind.  
  
## <a name="see-also"></a>Siehe auch  
 [Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster](../misc/announcing-property-window-selection-tracking.md)   
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)