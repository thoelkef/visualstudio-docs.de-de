---
title: Properties Window Fields and Interfaces | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2315310ed1ae5bbea748dabb5661384500941d0c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47512506"
---
# <a name="properties-window-fields-and-interfaces"></a>Felder und Schnittstellen des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Properties Window Fields and Interfaces](https://docs.microsoft.com/visualstudio/extensibility/internals/properties-window-fields-and-interfaces).  
  
Das Modell für die Auswahl, um zu bestimmen, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster basiert darauf, dass das Fenster, das Fokus, in der IDE besitzt. Alle Fenster und Objekt in das ausgewählte Fenster, haben die Auswahl Context-Objekt, die per Push an den globalen Auswahlkontext. Die Umgebung aktualisiert den Kontext für die globale Auswahl mit Werten aus einem Fensterrahmen, wenn das Fenster den Fokus hat. Wenn der Fokus geändert wird, steigt auch die Auswahlkontext.  
  
## <a name="tracking-selection-in-the-ide"></a>Nachverfolgen der Auswahl in der IDE  
 Der Fensterrahmen oder einem Standort im Besitz von der IDE bietet einen Dienst namens <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Die folgenden Schritte zeigen wie eine Änderung in einer auswahlanweisung, zurückzuführen, dass der Benutzer den Fokus zu einem anderen geöffneten Fenster ändern, oder wählen Sie ein anderes Projekt-Element in **Projektmappen-Explorer**, implementiert, um den Inhalt der Ändern **Eigenschaften** Fenster.  
  
1.  Das Objekt durch das VSPackage, die in den ausgewählten Fensters aufrufen positioniert wird, erstellt <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> damit <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Der Auswahlcontainer, angegeben durch das ausgewählte Fenster, erstellt eine eigene <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt. Wenn die Auswahl geändert wird, für das VSPackage aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> benachrichtigt alle Listener in der Umgebung, einschließlich der **Eigenschaften** Fenster der Änderung. Darüber hinaus den Zugriff auf die Hierarchie und Element-Informationen, die im Zusammenhang mit der neuen Auswahl.  
  
3.  Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und an Sie übergeben die Elemente der ausgewählten Hierarchie in der `VSHPROPID_BrowseObject` -Parameter auffüllt der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt.  
  
4.  Ein abgeleitetes Objekt aus der [IDispatch-Schnittstelle](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) wird zurückgegeben, für die <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> für das Element angefordert hat, und die Umgebung ihn in umschließt ein <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (Siehe den folgenden Schritt). Wenn der Aufruf fehlschlägt, wird die Umgebung einen zweiten Aufruf von `IVsHierarchy::GetProperty`, und übergeben sie den Auswahlcontainer <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , dass das Hierarchieelement oder die Elemente angeben.  
  
     Das Projekt, das VSPackage keine erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> da, die sie der Umgebung bereitgestellten Fenster VSPackage implementiert (z. B. **Projektmappen-Explorer**) erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in dessen Auftrag aufzubauen.  
  
5.  Die Umgebung Ruft die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> zum Abrufen der Objekte, die auf der Grundlage der `IDispatch` Schnittstelle zum Füllen der **Eigenschaften** Fenster.  
  
 Wenn ein Wert in der **Eigenschaften** Fenster geändert wird, die VSPackages implementieren, `IVsTrackSelectionEx::OnElementValueChangeEx` und `IVsTrackSelectionEx::OnSelectionChangeEx` , die Änderung an den Wert des Elements zu melden. Die Umgebung ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> im angezeigten Informationen zu den **Eigenschaften** Fenster mit den Eigenschaftswerten synchronisiert. Weitere Informationen finden Sie unter [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Zusätzlich zur Auswahl einer anderen Projektelement **Projektmappen-Explorer** zum Anzeigen von Eigenschaften in Bezug auf das Element, Sie können auch ein anderes Objekt aus, in einem Formular oder Dokument-Fenster, die mithilfe der Dropdown-Liste auf der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md).  
  
 Sie können ändern, dass die Möglichkeit, die Informationen, in angezeigt werden der **Eigenschaften** Raster von alphabetisch in eine Kategoriespalte, und, falls verfügbar, können Sie eine Eigenschaftenseite für ein ausgewähltes Objekt auch öffnen, indem Sie auf die entsprechenden Schaltflächen auf der  **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md) und [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
 Zum Schluss den unteren Rand der **Eigenschaften** Fenster enthält auch eine Beschreibung des Felds im ausgewählten der **Eigenschaften** Raster. Weitere Informationen finden Sie unter [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)

