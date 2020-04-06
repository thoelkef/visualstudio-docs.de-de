---
title: Eigenschaften Fensterfelder und Schnittstellen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, fields and interfaces
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9529708c781e7fdb04c3b4c5ee143b7605857e84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706166"
---
# <a name="properties-window-fields-and-interfaces"></a>Felder und Schnittstellen des Eigenschaftenfensters
Das Modell für die Auswahl, um zu bestimmen, welche Informationen im **Eigenschaftenfenster** angezeigt werden, basiert auf dem Fenster, das den Fokus in der IDE hat. In jedem Fenster und Objekt innerhalb des ausgewählten Fensters kann das Auswahlkontextobjekt in den globalen Auswahlkontext verschoben werden. Die Umgebung aktualisiert den globalen Auswahlkontext mit Werten aus einem Fensterrahmen, wenn dieses Fenster den Fokus hat. Wenn sich der Fokus ändert, ändert sich auch der Auswahlkontext.

## <a name="tracking-selection-in-the-ide"></a>Nachverfolgungsauswahl in der IDE
 Der Fensterrahmen oder die Website, die der <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>IDE gehört, verfügt über einen Dienst namens . Die folgenden Schritte zeigen, wie eine Änderung in einer Auswahl implementiert wird, die dadurch verursacht wird, dass der Benutzer den Fokus entweder auf ein anderes geöffnetes Fenster ändert oder ein anderes Projektelement im **Projektmappen-Explorer**auswählt, um den im **Eigenschaftenfenster** angezeigten Inhalt zu ändern.

1. Das von Ihrem VSPackage erstellte Objekt, das <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> in <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>den ausgewählten Fensteraufrufen mit aufgerufen wird, um aufgerufen zu haben.

2. Der Auswahlcontainer, der vom ausgewählten Fenster <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> bereitgestellt wird, erstellt ein eigenes Objekt. Wenn sich die Auswahl ändert, ruft das VSPackage alle Listener in der Umgebung, einschließlich des <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> **Eigenschaftenfensters,** auf, um alle Listener in der Umgebung über die Änderung zu benachrichtigen. Es bietet auch Zugriff auf Hierarchie- und Elementinformationen im Zusammenhang mit der neuen Auswahl.

3. Wenn <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> die ausgewählten Hierarchieelemente im `VSHPROPID_BrowseObject` Parameter aufgerufen und <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> übergeben werden, wird das Objekt aufgewirft.

4. Ein von der [IDispatch-Schnittstelle abgeleitetes](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) Objekt wird für [__VSHPROPID zurückgegeben. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) für das angeforderte Element, und <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> die Umgebung umschließt es in einen (siehe folgenden Schritt). Wenn der Aufruf fehlschlägt, ruft `IVsHierarchy::GetProperty`die Umgebung einen zweiten Aufruf von an , der den Auswahlcontainer [__VSHPROPID. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) die das Hierarchieelement oder die Artikel bereitstellen.

    Ihr Projekt VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird nicht erstellt, da das von der Umgebung bereitgestellte Fenster <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackage, das es implementiert (z. B. **Projektmappen-Explorer**), in seinem Namen erstellt wird.

5. Die Umgebung ruft die <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Methoden auf, um `IDispatch` die Objekte basierend auf der Schnittstelle abzurufen, die im **Eigenschaftenfenster** ausgefüllt werden soll.

   Wenn ein Wert im **Eigenschaftenfenster** geändert `IVsTrackSelectionEx::OnElementValueChangeEx` wird, implementieren und `IVsTrackSelectionEx::OnSelectionChangeEx` melden VSPackages die Änderung an den Elementwert. Die Umgebung ruft <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> dann die im **Eigenschaftenfenster** angezeigten Informationen auf oder hält sie mit den Eigenschaftswerten synchronisiert. Weitere Informationen finden Sie unter [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](#updating-property-values-in-the-properties-window).

   Zusätzlich zur Auswahl eines anderen Projektelements im **Projektmappen-Explorer** zum Anzeigen von Eigenschaften, die sich auf dieses Element beziehen, können Sie auch ein anderes Objekt in einem Formular- oder Dokumentfenster auswählen, indem Sie die Dropdownliste verwenden, die im **Fenster Eigenschaften** verfügbar ist. Weitere Informationen finden Sie unter [Eigenschaftenfensterobjektliste](../../extensibility/internals/properties-window-object-list.md).

   Sie können die Anzeige von Informationen im **Fensterraster Eigenschaften** von alphabetisch in kategorial ändern, und wenn verfügbar, können Sie auch eine Eigenschaftenseite für ein ausgewähltes Objekt öffnen, indem Sie auf die entsprechenden Schaltflächen im **Eigenschaftenfenster** klicken. Weitere Informationen finden Sie unter [Eigenschaftenfensterschaltflächen](../../extensibility/internals/properties-window-buttons.md) und [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).

   Schließlich enthält der untere Rand des **Eigenschaftenfensters** auch eine Beschreibung des feldes, das im **Fensterraster Eigenschaften** ausgewählt wurde. Weitere Informationen finden Sie unter [Abrufen von Feldbeschreibungen aus dem Eigenschaftenfenster](#getting-field-descriptions-from-the-properties-window).

## <a name="updating-property-values-in-the-properties-window"></a><a name="updating-property-values-in-the-properties-window"></a>Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster
Es gibt zwei Möglichkeiten, das **Eigenschaften** -Fenster ständig mit Änderungen von Eigenschaftswerten zu synchronisieren. Die erste besteht darin, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>-Schnittstelle aufzurufen, die Zugriff auf die grundlegende Fensterverwaltungsfunktionalität bietet, einschließlich Zugriff auf und Erstellung von Tool- und Dokumentfenstern, die von der Umgebung bereitgestellt werden. In den folgenden Schritten ist dieser Synchronisierungsprozess beschrieben.

### <a name="updating-property-values-using-ivsuishell"></a>Aktualisieren von Eigenschaftswerten über IVsUIShell

#### <a name="to-update-property-values-using-the-ivsuishell-interface"></a>So aktualisieren Sie Eigenschaftswerte über die IVsUIShell-Schnittstelle

1. Rufen Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> (über den <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>-Dienst) jedes Mal auf, wenn VSPackages, Projekte oder Editoren Tool- oder Dokumentfenster erstellen oder durchlaufen müssen.

2. Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.RefreshPropertyBrowser%2A> Sie, um das **Eigenschaftenfenster** mit Eigenschaftenänderungen für ein Projekt (oder ein anderes <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> ausgewähltes <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink.OnChanged%2A> Objekt, das vom **Eigenschaftenfenster** durchsucht wird) zu synchronisieren, ohne Ereignisse zu implementieren und zu auslösen.

3. Implementieren Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>-Methoden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.AdviseHierarchyEvents%2A> und <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.UnadviseHierarchyEvents%2A>, um Clientbenachrichtigung zu Hierarchieereignissen einzurichten bzw. zu deaktivieren, ohne dass für die Hierarchie <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> implementiert werden muss.

### <a name="updating-property-values-using-iconnection"></a>Aktualisieren von Eigenschaftswerten über IConnection
 Die zweite Möglichkeit, das **Eigenschaften** -Fenster ständig mit Eigenschaftswertänderungen zu synchronisieren, besteht darin, `IConnection` für das verbindungsfähige Objekt zu implementieren, um das Vorhandensein der Ausgangsschnittstellen anzugeben. Wenn Sie den Eigenschaftsnamen lokalisieren möchten, leiten Sie das Objekt aus <xref:System.ComponentModel.ICustomTypeDescriptor> ab. Die <xref:System.ComponentModel.ICustomTypeDescriptor>-Implementierung kann die von ihr zurückgegebenen Eigenschaftsdeskriptoren sowie den Namen einer Eigenschaft ändern. Wenn Sie die Beschreibung lokalisieren möchten, erstellen Sie ein Attribut, das aus <xref:System.ComponentModel.DescriptionAttribute> abgeleitet wird, und überschreiben Sie die Description-Eigenschaft.

#### <a name="considerations-in-implementing-the-iconnection-interface"></a>Aspekte zur Implementierung der IConnection-Schnittstelle

1. `IConnection` bietet Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle. Die Schnittstelle bietet außerdem Zugriff auf alle Verbindungspunktunterobjekte, von denen jedes die <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle implementiert.

2. Für jedes Browseobjekt muss ein <xref:Microsoft.VisualStudio.OLE.Interop.IPropertyNotifySink>-Ereignis implementiert werden. Im **Eigenschaften** -Fenster erfolgt eine Empfehlung für das Ereignis, das über `IConnection`festgelegt ist.

3. Ein Verbindungspunkt steuert, wie viele Verbindungen in seiner Implementierung von <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.Advise%2A> zulässig sind. Ein Verbindungspunkt, der nur eine Schnittstelle zulässt, kann <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> aus der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint.EnumConnections%2A>-Methode zurückgeben.

4. Ein Client kann die `IConnection`-Schnittstelle aufrufen, um Zugriff auf ein Enumeratorunterobjekt mit der <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle zu erhalten. Die <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnectionPoints>-Schnittstelle kann dann aufgerufen werden, um Verbindungspunkte für jede Ausgangsschnittstellen-ID (IID) zu durchlaufen.

5. `IConnection` kann auch aufgerufen werden, um mit der <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint>-Schnittstelle Zugriff auf Verbindungspunktunterobjekte für jede ausgehende IID zu erhalten. Über <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> die Schnittstelle startet oder beendet ein Client eine Beratungsschleife mit dem anschließbaren Objekt und der eigenen Synchronisierung des Clients. Der Client kann <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPoint> auch die Schnittstelle aufrufen, um ein <xref:Microsoft.VisualStudio.OLE.Interop.IEnumConnections> Enumeratorobjekt mit der Schnittstelle zu erhalten, um die Verbindungen aufzuzählen, die er kennt.

## <a name="getting-field-descriptions-from-the-properties-window"></a><a name="getting-field-descriptions-from-the-properties-window"></a>Abrufen von Feldbeschreibungen aus dem Eigenschaftenfenster
Am unteren Rand des Fensters **Eigenschaften** werden in einem Beschreibungsbereich Informationen angezeigt, die zu dem ausgewählten Eigenschaftenfeld gehören. Diese Funktion ist standardmäßig aktiviert. Wenn Sie das Beschreibungsfeld ausblenden möchten, klicken Sie mit der rechten Maustaste in das Fenster **Eigenschaften** , und klicken Sie auf **Beschreibung**. Dies bewirkt auch, dass das Häkchen neben dem Titel **Beschreibung** im Menüfenster entfernt wird. Sie können das Feld wieder anzeigen, indem die gleichen Schritte ausführen, um **Beschreibung** erneut zu aktivieren.

 Die Informationen im Beschreibungsfeld stammen aus <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>. Jede Methode, Schnittstelle, Co-Klasse usw. kann ein nicht lokalisiertes `helpstring` Attribut in der Typbibliothek haben. Das **Eigenschaftenfenster** ruft die <xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo.GetDocumentation%2A>Zeichenfolge aus ab.

### <a name="to-specify-localized-help-strings"></a>So geben Sie lokalisierte Hilfetexte (Hilfezeichenfolgen) an

1. Fügen Sie das `helpstringdll` -Attribut zur library-Anweisung in der Typbibliothek (`typelib`) hinzu.

   > [!NOTE]
   > Dieser Schritt ist optional, wenn sich die Typbibliothek in einer Objektbibliotheksdatei (OLB-Datei) befindet.

2. Geben Sie `helpstringcontext` -Attribute für die Zeichenfolgen an. Sie können auch `helpstring` -Attribute angeben.

    Diese Attribute unterscheiden sich von den Attributen `helpfile` und `helpcontext` , die in den jeweiligen Hilfethemen in CHM-Datei enthalten sind.

   Um die Beschreibungsinformationen abzurufen, die für den <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2.GetDocumentation2%2A> markierten Eigenschaftsnamen angezeigt werden `lcid` sollen, ruft das **Eigenschaftenfenster** die ausgewählte Eigenschaft auf und gibt das gewünschte Attribut für die Ausgabezeichenfolge an. Intern findet <xref:System.Runtime.InteropServices.ComTypes.ITypeInfo2> die DLL-Datei, die im `helpstringdll`-Attribut angegeben ist, und ruft `DLLGetDocumentation` für diese DLL-Datei mit dem angegebenen Kontext und `lcid`-Attribut auf.

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

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
