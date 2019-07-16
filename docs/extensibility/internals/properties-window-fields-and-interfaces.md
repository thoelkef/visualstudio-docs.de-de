---
title: Properties Window Fields and Interfaces | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 379eaa6e154b77d10463514a63978708bf2b89d0
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66347881"
---
# <a name="properties-window-fields-and-interfaces"></a>Felder und Schnittstellen des Eigenschaftenfensters
Das Modell für die Auswahl, um zu bestimmen, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster basiert darauf, dass das Fenster, das Fokus, in der IDE besitzt. Alle Fenster und Objekt in das ausgewählte Fenster, haben die Auswahl Context-Objekt, die per Push an den globalen Auswahlkontext. Die Umgebung aktualisiert den Kontext für die globale Auswahl mit Werten aus einem Fensterrahmen, wenn das Fenster den Fokus hat. Wenn der Fokus geändert wird, steigt auch die Auswahlkontext.

## <a name="tracking-selection-in-the-ide"></a>Nachverfolgen der Auswahl in der IDE
 Der Fensterrahmen oder einem Standort im Besitz von der IDE bietet einen Dienst namens <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>. Die folgenden Schritte zeigen wie eine Änderung in einer auswahlanweisung, zurückzuführen, dass der Benutzer den Fokus zu einem anderen geöffneten Fenster ändern, oder wählen Sie ein anderes Projekt-Element in **Projektmappen-Explorer**, implementiert, um den Inhalt der Ändern **Eigenschaften** Fenster.

1. Das Objekt durch das VSPackage, die in den ausgewählten Fensters aufrufen positioniert wird, erstellt <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> damit <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Aufrufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>.

2. Der Auswahlcontainer, angegeben durch das ausgewählte Fenster, erstellt eine eigene <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt. Wenn die Auswahl geändert wird, für das VSPackage aufgerufen <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> benachrichtigt alle Listener in der Umgebung, einschließlich der **Eigenschaften** Fenster der Änderung. Darüber hinaus den Zugriff auf die Hierarchie und Element-Informationen, die im Zusammenhang mit der neuen Auswahl.

3. Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und an Sie übergeben die Elemente der ausgewählten Hierarchie in der `VSHPROPID_BrowseObject` -Parameter auffüllt der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Objekt.

4. Ein Objekt, abgeleitet aus den [IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) wird zurückgegeben, für die [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) für das Element angefordert hat, und die Umgebung ihn in umschließt ein <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> (Siehe den folgenden Schritt). Wenn der Aufruf fehlschlägt, wird die Umgebung einen zweiten Aufruf von `IVsHierarchy::GetProperty`, und übergeben sie den Auswahlcontainer [__VSHPROPID. VSHPROPID_SelContainer](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) , dass das Hierarchieelement oder die Elemente angeben.

    Das Projekt, das VSPackage keine erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> da, die sie der Umgebung bereitgestellten Fenster VSPackage implementiert (z. B. **Projektmappen-Explorer**) erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in dessen Auftrag aufzubauen.

5. Die Umgebung Ruft die Methoden der <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> zum Abrufen der Objekte, die auf der Grundlage der `IDispatch` Schnittstelle zum Füllen der **Eigenschaften** Fenster.

   Wenn ein Wert in der **Eigenschaften** Fenster geändert wird, die VSPackages implementieren, `IVsTrackSelectionEx::OnElementValueChangeEx` und `IVsTrackSelectionEx::OnSelectionChangeEx` , die Änderung an den Wert des Elements zu melden. Die Umgebung ruft dann <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> im angezeigten Informationen zu den **Eigenschaften** Fenster mit den Eigenschaftswerten synchronisiert. Weitere Informationen finden Sie unter [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](#updating-property-values-in-the-properties-window).

   Zusätzlich zur Auswahl einer anderen Projektelement **Projektmappen-Explorer** zum Anzeigen von Eigenschaften in Bezug auf das Element, Sie können auch ein anderes Objekt aus, in einem Formular oder Dokument-Fenster, die mithilfe der Dropdown-Liste auf der **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md).

   Sie können ändern, dass die Möglichkeit, die Informationen, in angezeigt werden der **Eigenschaften** Raster von alphabetisch in eine Kategoriespalte, und, falls verfügbar, können Sie eine Eigenschaftenseite für ein ausgewähltes Objekt auch öffnen, indem Sie auf die entsprechenden Schaltflächen auf der  **Eigenschaften** Fenster. Weitere Informationen finden Sie unter [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md) und [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).

   Zum Schluss den unteren Rand der **Eigenschaften** Fenster enthält auch eine Beschreibung des Felds im ausgewählten der **Eigenschaften** Raster. Weitere Informationen finden Sie unter [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a> Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Die erste besteht darin, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle aufzurufen, die Zugriff auf die grundlegende Fensterverwaltungsfunktionalität bietet, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenstern, die von der Umgebung bereitgestellt werden. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Dienst) jedes Mal auf, wenn VSPackages, Projekte oder Editoren Tool- oder Dokumentfenster erstellen oder durchlaufen müssen.

2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> zu der **Eigenschaften** Fensters mit eigenschaftsänderungen für ein Projekt (oder ein anderes Objekt durchsucht werden, indem die **Eigenschaften** Fenster) ohne die Implementierung der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> und das Auslösen von <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> Ereignisse.

3. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>, um Clientbenachrichtigung zu Hierarchieereignissen einzurichten bzw. zu deaktivieren, ohne dass für die Hierarchie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> implementiert werden muss.

### <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor> ab. Die <xref:System.ComponentModel.ICustomTypeDescriptor>-Implementierung kann die von ihr zurückgegebenen Eigenschaftsdeskriptoren sowie den Namen einer Eigenschaft ändern. Wenn Sie die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das aus <xref:System.ComponentModel.DescriptionAttribute> abgeleitet wird, und überschreiben Sie die Description-Eigenschaft.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle

1. `IConnection` bietet Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle. Die Schnittstelle bietet außerdem Zugriff auf alle Verbindungspunktunterobjekte, von denen jedes die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle implementiert.

2. Für jedes Browseobjekt muss ein <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>-Ereignis implementiert werden. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.

3. Ein Verbindungspunkt steuert, wie viele Verbindungen in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> zulässig sind. Ein Verbindungspunkt, der nur eine Schnittstelle zulässt, kann <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>-Methode zurückgeben.

4. Ein Client kann die `IConnection`-Schnittstelle aufrufen, um Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle zu erhalten. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) zu durchlaufen.

5. `IConnection` kann auch aufgerufen werden, um mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle Zugriff auf Verbindungspunktunterobjekte für jede ausgehende IID zu erhalten. Über die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle, startet oder beendet ein Client eine Empfehlungsschleife mit dem verbindungsfähigen Objekt und der Synchronisierung des Clients. Der Client kann auch die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle aufrufen, um ein Enumeratorobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections>-Schnittstelle abzurufen, damit er die ihm bekannten Verbindungen durchlaufen kann.

## <a name="getting-field-descriptions-from-the-properties-window"></a> Abrufen von Feldbeschreibungen im Eigenschaftenfenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften** , und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.

 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co-Klasse usw. kann ein nicht lokalisiertes `helpstring` Attribut in der Typbibliothek haben. Die **Eigenschaften** Fenster Ruft die Zeichenfolge aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>.

### <a name="to-specify-localized-help-strings"></a>So geben Sie lokalisierte Hilfetexte (Hilfezeichenfolgen) an

1. Fügen Sie das `helpstringdll` -Attribut zur library-Anweisung in der Typbibliothek (`typelib`) hinzu.

   > [!NOTE]
   > Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei (OLB-Datei) befindet.

2. Geben Sie `helpstringcontext` -Attribute für die Zeichenfolgen an. Sie können auch `helpstring` -Attribute angeben.

    Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext` , die in den jeweiligen Hilfethemen in CHM-Datei enthalten sind.

   Zum Abrufen der Beschreibungsinformationen für den markierten Eigenschaftennamen angezeigt werden soll die **Eigenschaften** Fenster Aufrufe <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> für die Eigenschaft, die ausgewählt ist, wobei Sie das gewünschte `lcid` -Attribut für die Ausgabezeichenfolge. Intern findet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> die DLL-Datei, die im `helpstringdll`-Attribut angegeben ist, und ruft `DLLGetDocumentation` für diese DLL-Datei mit dem angegebenen Kontext und `lcid`-Attribut auf.

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

 Eine weitere Möglichkeit zum Abrufen des lokalisierten Namens und der lokalisierten Beschreibung einer Eigenschaft besteht darin, <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.GetLocalizedPropertyInfo%2A> zu implementieren. Weitere Informationen über die Implementierung dieser Methode finden Sie unter [Properties Window Fields and Interfaces](../../extensibility/internals/properties-window-fields-and-interfaces.md).

## <a name="see-also"></a>Siehe auch

- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)