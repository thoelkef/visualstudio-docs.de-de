---
title: Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- Properties window, updating property values
- property values, updating in Properties window
ms.assetid: 9358e8c3-b9d2-4fd4-aaab-cf48d1526db4
caps.latest.revision: 9
manager: jillfra
ms.openlocfilehash: 18ecf0a21c5b2d73bdf8e439d25765b6b275cbd9
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/22/2019
ms.locfileid: "60080554"
---
# <a name="updating-property-values-in-the-properties-window"></a>Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Die erste besteht darin, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle aufzurufen, die Zugriff auf die grundlegende Fensterverwaltungsfunktionalität bietet, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenstern, die von der Umgebung bereitgestellt werden. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.  
  
## <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle  
  
1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Dienst) jedes Mal auf, wenn VSPackages, Projekte oder Editoren Tool- oder Dokumentfenster erstellen oder durchlaufen müssen.  
  
2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zu der **Eigenschaften** Fensters mit eigenschaftsänderungen für ein Projekt (oder ein anderes Objekt durchsucht werden, indem die **Eigenschaften** Fenster) ohne die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und das Auslösen von <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> Ereignisse.  
  
3. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>, um Clientbenachrichtigung zu Hierarchieereignissen einzurichten bzw. zu deaktivieren, ohne dass für die Hierarchie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> implementiert werden muss.  
  
## <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection  
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor> ab. Die <xref:System.ComponentModel.ICustomTypeDescriptor>-Implementierung kann die von ihr zurückgegebenen Eigenschaftsdeskriptoren sowie den Namen einer Eigenschaft ändern. Wenn Sie die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das aus <xref:System.ComponentModel.DescriptionAttribute> abgeleitet wird, und überschreiben Sie die Description-Eigenschaft.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle  
  
1. `IConnection` bietet Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle. Die Schnittstelle bietet außerdem Zugriff auf alle Verbindungspunktunterobjekte, von denen jedes die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle implementiert.  
  
2. Für jedes Browseobjekt muss ein <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>-Ereignis implementiert werden. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.  
  
3. Ein Verbindungspunkt steuert, wie viele Verbindungen in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> zulässig sind. Ein Verbindungspunkt, der nur eine Schnittstelle zulässt, kann <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>-Methode zurückgeben.  
  
4. Ein Client kann die `IConnection`-Schnittstelle aufrufen, um Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle zu erhalten. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) zu durchlaufen.  
  
5. `IConnection` kann auch aufgerufen werden, um mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle Zugriff auf Verbindungspunktunterobjekte für jede ausgehende IID zu erhalten. Über die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle, startet oder beendet ein Client eine Empfehlungsschleife mit dem verbindungsfähigen Objekt und der Synchronisierung des Clients. Der Client kann auch die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle aufrufen, um ein Enumeratorobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>-Schnittstelle abzurufen, damit er die ihm bekannten Verbindungen durchlaufen kann.  
  
## <a name="see-also"></a>Siehe auch  
 [Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster](../misc/announcing-property-window-selection-tracking.md)   
 [Erweitern von Eigenschaften](../extensibility/internals/extending-properties.md)