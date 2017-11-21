---
title: "Felder für die Anwendungseigenschaften Fenster und Schnittstellen | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: a4dd37d33230be758bd5a5adf6f5e10d5a978800
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="properties-window-fields-and-interfaces"></a>Felder für die Anwendungseigenschaften Fenster und Schnittstellen
Das Modell für die Auswahl, um zu bestimmen, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster basiert darauf, dass das Fenster, in der IDE den Fokus besitzt. Jedes Fenster und das Objekt in das ausgewählte Fenster kann ihre Auswahl Context-Objekt an den Kontext der globalen Auswahl abgelegt haben. Die Umgebung aktualisiert den globalen Auswahlkontext mit Werten aus einem Fensterrahmen, wenn das Fenster den Fokus besitzt. Wenn der Fokus geändert wird, gilt dies auch die Auswahlkontext.  
  
## <a name="tracking-selection-in-the-ide"></a>Nachverfolgen der Auswahl in der IDE  
 Der Fensterrahmen oder Website, im Besitz von der IDE verfügt über einen Dienst namens <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Die folgenden Schritte zeigen wie eine Änderung in einer Markierung, durch den Benutzer ändert den Fokus zu einem anderen geöffneten Fenster oder Auswahl eines anderen Projekts in verursacht **Projektmappen-Explorer**, wird implementiert, um den Inhalt in die Ändern **Eigenschaften** Fenster.  
  
1.  Das Objekt erstellt, indem das VSPackage, die in den Aufrufen für die ausgewählte Fenster positioniert wird <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> haben <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.  
  
2.  Durch das ausgewählte Fenster angegebene Auswahlcontainer erstellt einen eigenen <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt. Wenn die Menüauswahl ändert sich, das VSPackage aufruft, <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> an alle Listener in der Umgebung zu benachrichtigen einschließlich der **Eigenschaften** Fenster der Änderung. Darüber hinaus den Zugriff auf die Hierarchie und Element-Informationen im Zusammenhang mit der die neue Auswahl.  
  
3.  Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und zur Übergabe an die ausgewählte Hierarchieelemente in der `VSHPROPID_BrowseObject` -Parameter auffüllt der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt.  
  
4.  Ein abgeleitetes Objekt aus der [IDispatch-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx) zurückgegebenen <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> für das Element angefordert, und die Umgebung ihn in umschließt ein <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (Siehe den folgenden Schritt). Wenn der Aufruf fehlschlägt, wird die Umgebung einen zweiten Aufruf von `IVsHierarchy::GetProperty`, und übergeben sie die Auswahlcontainer <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , dass die Hierarchieelement oder Elemente angeben.  
  
     Das Projekt, das VSPackage keine erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> da, die sie im Fenster Umgebung bereitgestellte VSPackage implementiert (z. B. **Projektmappen-Explorer**) erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in dessen Auftrag aufzubauen.  
  
5.  Die Umgebung Ruft die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> zum Abrufen der Objekte, die auf der Grundlage der `IDispatch` Schnittstelle zum Füllen der **Eigenschaften** Fenster.  
  
 Wenn ein Wert in der **Eigenschaften** Fenster geändert wird, Implementieren von VSPackages `IVsTrackSelectionEx::OnElementValueChangeEx` und `IVsTrackSelectionEx::OnSelectionChangeEx` die Änderung an den Elementwert zu melden. Klicken Sie dann die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> in angezeigten Informationen zu den **Eigenschaften** Fenster mit den Eigenschaftswerten synchronisiert. Weitere Informationen finden Sie unter [aktualisiert Eigenschaftswerte im Eigenschaftenfenster](#updating-property-values-in-the-properties-window).  
  
 Zusätzlich zur Auswahl einer anderen Projektelement **Projektmappen-Explorer** zum Anzeigen von Eigenschaften im Zusammenhang mit diesem Element Wunsch können Sie ein anderes Objekt aus, in einem Formular oder Dokument-Fenster, die mithilfe der Dropdown-Liste auf die **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Liste der Eigenschaften im Fenster Objekt](../../extensibility/internals/properties-window-object-list.md).  
  
 Sie können ändern, wie Informationen, in angezeigt wird der **Eigenschaften** Fenster Raster aus alphabetischer "categorical", und, falls verfügbar, können Sie eine Eigenschaftenseite für ein ausgewähltes Objekt auch öffnen, indem Sie auf die entsprechenden Schaltflächen auf der  **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Eigenschaften im Fenster Schaltflächen](../../extensibility/internals/properties-window-buttons.md) und [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
 Schließlich den unteren Rand der **Eigenschaften** Fenster enthält auch eine Beschreibung des Felds im ausgewählten der **Eigenschaften** Fenster Raster. Weitere Informationen finden Sie unter [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](#getting-field-descriptions-from-the-properties-window).  
  
## <a name="updating-property-values-in-the-properties-window"></a>Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Der erste Schritt besteht im Aufrufen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> -Schnittstelle, die Zugriff auf grundlegende fensterverwaltungsfunktionalität bietet, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenster Windows, die von der Umgebung bereitgestellt. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.  
  
### <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell  
  
#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle  
  
1.  Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell> Dienst) jedes Mal, wenn VSPackages, Projekte oder Editoren erstellen oder Tool-oder Dokumentfenster durchlaufen müssen.  
  
2.  Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> beibehalten der **Eigenschaften** -Fenster ständig mit eigenschaftsänderungen für ein Projekt (oder ein anderes Objekt durchsucht wird, indem die **Eigenschaften** Fenster) ohne implementieren<xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und das Auslösen von <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> Ereignisse.  
  
3.  Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A> zur Herstellung einer deaktivieren bzw. Clientbenachrichtigung von Hierarchieereignisse, ohne dass der Hierarchie implementieren <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer>.  
  
### <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection  
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor>. Die <xref:System.ComponentModel.ICustomTypeDescriptor> Implementierung der zurückgegebenen Eigenschaftsdeskriptoren ändern kann, und ändern Sie den Namen einer Eigenschaft. Um die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das von abgeleitet ist <xref:System.ComponentModel.DescriptionAttribute> und überschreiben die Description-Eigenschaft.  
  
#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle  
  
1.  `IConnection`ermöglicht den Zugriff auf ein enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle. Es bietet außerdem Zugriff auf alle die verbindungspunktunterobjekte, aller implementiert die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle.  
  
2.  Ein Objekt zum Durchsuchen ist verantwortlich für die Implementierung einer <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink> Ereignis. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.  
  
3.  Ein Verbindungspunkt steuert, wie viele Verbindungen (mindestens) ermöglicht es in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A>. Kann ein Verbindungspunkt, der nur eine Schnittstelle zulässt zurückgeben <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A> Methode.  
  
4.  Ein Client aufrufen kann die `IConnection` Schnittstelle zum Abrufen der Zugriff auf ein enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints> Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) aufgelistet werden.  
  
5.  `IConnection`kann auch aufgerufen werden, um Zugriff auf verbindungspunktunterobjekte mit erhalten die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle für jede ausgehende IID. Über die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle, ein Client startet oder beendet eine empfehlungsschleife mit dem verbindungsfähigen Objekt und der Synchronisierung des Clients. Der Client kann auch Aufrufen der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> Schnittstelle, um ein Enumeratorobjekt mit erhalten die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> Schnittstelle, um die Verbindungen aufgelistet, die es bekannt.  
  
## <a name="getting-field-descriptions-from-the-properties-window"></a>Abrufen von Feldbeschreibungen im Eigenschaftenfenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften** , und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.  
  
 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co-Klasse usw. kann ein nicht lokalisiertes `helpstring` Attribut in der Typbibliothek haben. Die **Eigenschaften** Fenster Ruft die Zeichenfolge aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.  
  
### <a name="to-specify-localized-help-strings"></a>So geben Sie lokalisierte Hilfetexte (Hilfezeichenfolgen) an  
  
1.  Fügen Sie das `helpstringdll` -Attribut zur library-Anweisung in der Typbibliothek (`typelib`) hinzu.  
  
    > [!NOTE]
    >  Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei (OLB-Datei) befindet.  
  
2.  Geben Sie `helpstringcontext` -Attribute für die Zeichenfolgen an. Sie können auch `helpstring` -Attribute angeben.  
  
     Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext` , die in den jeweiligen Hilfethemen in CHM-Datei enthalten sind.  
  
 Zum Abrufen der Beschreibungsinformationen für den markierten Eigenschaftennamen angezeigt werden soll die **Eigenschaften** Fenster Aufrufe <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> für die Eigenschaft, die ausgewählt wird, wobei Sie das gewünschte `lcid` -Attribut für die Ausgabezeichenfolge. Intern <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> sucht den DLL-Datei im angegebenen der `helpstringdll` Attribut und ruft `DLLGetDocumentation` für diese DLL-Datei mit dem angegebenen Kontext und `lcid` Attribut.  
  
 Die Signatur und die Implementierung von `DLLGetDocumentation` sind:  
  
```cpp  
STDAPI DLLGetDocumentation  
(  
   ITypeLib * /* ptlib */,  
   ITypeInfo * /* ptinfo */,  
   LCID /* lcid */,  
   DWORD dwCtx,  
   BSTR * pbstrHelpString  
);  
```  
  
 Die `DLLGetDocumentation` -Funktion muss ein Export sein, der in der DEF-Datei für die DLL-Datei definiert ist.  
  
 Intern wird eine OLB-Datei erstellt, die tatsächlich eine DLL ist. Diese DLL enthält eine Ressource, die Typbibliotheksdatei (TLB-Datei), und eine exportierte Funktion, `DLLGetDocumentation`.  
  
 Im Fall von OLB-Dateien ist das `helpstringdll` Attribut optional, weil es dieselbe Datei angibt, die selbst die TLB-Datei enthält.  
  
 Wenn Sie möchten, dass Zeichenfolgen abgerufen und im Bereich **Beschreibung** angezeigt werden, ist es daher mindestens erforderlich, dass Sie das `helpstring` -Attribut in der Typbibliothek angeben. Sollen diese Zeichenfolgen lokalisiert sein, müssen Sie das (optionale) `helpstringdll` -Attribut und das (erforderliche) `helpstringcontext` -Attribut angeben sowie `DLLGetDocumentation`implementieren.  
  
 Es gibt keine weiteren Schnittstellen, die implementiert werden müssen, wenn lokalisierte Informationen über das `helpstringcontext` -Attribut und `DLLGetDocumentation`abgerufen werden.  
  
 Eine weitere Möglichkeit zum Abrufen der lokalisierten Namen und eine Beschreibung einer Eigenschaft besteht in der Implementierung <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A>. Weitere Informationen über die Implementierung dieser Methode finden Sie unter [Eigenschaften im Fenster Felder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md).  

## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)