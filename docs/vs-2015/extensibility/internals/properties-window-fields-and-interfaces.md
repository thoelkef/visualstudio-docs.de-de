---
title: Felder und Schnittstellen des Eigenschaften Fensters | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b58314d64536ecf33cc5589609ee5524a9352629
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65700824"
---
# <a name="properties-window-fields-and-interfaces"></a>Felder und Schnittstellen des Eigenschaftenfensters
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das Modell für die Auswahl, um zu bestimmen, welche Informationen im **Eigenschaften** Fenster angezeigt werden, basiert auf dem Fenster, das in der IDE den Fokus besitzt. Jedes Fenster und Objekt innerhalb des ausgewählten Fensters können das Auswahl Kontext Objekt in den globalen Auswahl Kontext übermittelt haben. Die Umgebung aktualisiert den globalen Auswahl Kontext mit Werten aus einem Fensterrahmen, wenn dieses Fenster den Fokus besitzt. Wenn sich der Fokus ändert, wird der Auswahl Kontext angezeigt.  
  
## <a name="tracking-selection-in-the-ide"></a>Nachverfolgen der Auswahl in der IDE  
 Der Fensterrahmen oder die Website, der im Besitz der IDE ist, verfügt über einen Dienst mit dem Namen <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> . Die folgenden Schritte zeigen, wie eine Änderung in einer Auswahl, die durch den Benutzer bewirkt wird, dass der Fokus entweder auf ein anderes geöffnetes Fenster wechselt, oder das Auswählen eines anderen Projekt Elements in **Projektmappen-Explorer**implementiert wird, damit der im **Eigenschaften** Fenster angezeigte Inhalt geändert wird.  
  
1. Das-Objekt, das von Ihrem VSPackage erstellt wird, das im ausgewählten Fenster angezeigt wird <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> , um aufrufen zu können <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection> .  
  
2. Der Auswahl Container, der vom ausgewählten Fenster bereitgestellt wird, erstellt ein eigenes- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt. Wenn sich die Auswahl ändert, ruft das VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> auf, um alle Listener in der Umgebung (einschließlich des **Eigenschaften** Fensters) der Änderung zu benachrichtigen. Sie ermöglicht außerdem den Zugriff auf Hierarchie-und Element Informationen im Zusammenhang mit der neuen Auswahl.  
  
3. Durch Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und übergeben der ausgewählten Hierarchie Elemente im- `VSHPROPID_BrowseObject` Parameter wird das-Objekt aufgefüllt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> .  
  
4. Ein von der [IDispatch-Schnittstelle](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) abgeleitetes Objekt wird für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> das angeforderte Element zurückgegeben, und die Umgebung umschließt es in eine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (siehe folgenden Schritt). Wenn der-Befehl fehlschlägt, führt die Umgebung einen zweiten-Aufrufvorgang aus `IVsHierarchy::GetProperty` und übergibt ihn an den Auswahl Container, <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> den die Elemente der Hierarchie bereitstellen.  
  
    Das VSPackage für das Projekt wird nicht erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , weil das von der Umgebung bereitgestellte Fenster VSPackage, das es implementiert (z. b. **Projektmappen-Explorer**), <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in seinem Namen erstellt wird.  
  
5. Die Umgebung Ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> auf, um die Objekte auf der Grundlage der- `IDispatch` Schnittstelle zu erhalten, die im **Eigenschaften** Fenster ausgefüllt werden soll.  
  
   Wenn ein Wert im **Eigenschaften** Fenster geändert wird, implementieren VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` und, `IVsTrackSelectionEx::OnSelectionChangeEx` um die Änderung an den Elementwert zu melden. Dann ruft die Umgebung <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> auf, um die im **Eigenschaften** Fenster angezeigten Informationen mit den Eigenschafts Werten zu synchronisieren. Weitere Informationen finden Sie unter [Aktualisieren von Eigenschafts Werten im Eigenschaften Fenster](../../misc/updating-property-values-in-the-properties-window.md).  
  
   Sie können nicht nur ein anderes Projekt Element in **Projektmappen-Explorer** auswählen, um Eigenschaften anzuzeigen, die mit diesem Element verknüpft sind. Sie können auch ein anderes Objekt innerhalb eines Formular-oder Dokument Fensters mithilfe der Dropdown Liste auswählen, die im **Eigenschaften** Fenster verfügbar ist. Weitere Informationen finden Sie in der [Objektliste Eigenschaften Fenster](../../extensibility/internals/properties-window-object-list.md).  
  
   Sie können die Anzeige von Informationen im Fenster **Eigenschaften** Fenster von alphabetisch zu kategorischer Seite ändern. Wenn Sie verfügbar sind, können Sie auch eine Eigenschaften Seite für ein ausgewähltes Objekt öffnen, indem Sie auf die entsprechenden Schaltflächen im **Eigenschaften** Fenster klicken. Weitere Informationen finden Sie unter [Eigenschaften Fenster](../../extensibility/internals/properties-window-buttons.md) Schaltflächen und Eigenschaften [Seiten](../../extensibility/internals/property-pages.md).  
  
   Schließlich enthält das Ende des Fensters **Eigenschaften** auch eine Beschreibung des Felds, das im Fenster **Eigenschaften** Fenster ausgewählt wurde. Weitere Informationen finden Sie unter [erhalten von Feldbeschreibungen aus dem Eigenschaften Fenster](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## <a name="see-also"></a>Weitere Informationen  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
