---
title: "Eigenschaften-Fenster Felder und Schnittstellen | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Im Eigenschaftenfenster, Felder und Schnittstellen"
ms.assetid: 0328f0e5-2380-4a7a-a872-b547cb775050
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Eigenschaften-Fenster Felder und Schnittstellen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das Modell, für die Auswahl, welche Informationen im **Eigenschaften** Fenster angezeigt wird, basiert auf das Fenster, das den Fokus in der IDE hat.  Jedes Fenster und \- Objekt innerhalb des ausgewählten Fensters sein können, für die Auswahl, die auf den globalen Auswahlkontext gedrückt wird.  Die Umgebung aktualisiert den globalen Auswahlkontext mit Werten aus einem Fensterrahmen, wenn dieses Fenster den Fokus besitzt.  Wenn der Fokus geändert wird, hat dies den Auswahlkontext.  
  
## Nachverfolgungs\-Auswahl in der IDE  
 Der Fensterrahmen oder die Website, die von der IDE gehört, ist ein Dienst, der <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection>aufgerufen wird.  Die folgenden Schritte zeigen, wie eine Änderung einer Auswahl des Benutzers bewirkt, dass entweder der Fokus zu einem anderen geöffneten Fenstern ändern oder ein anderes Projektelement in **Projektmappen\-Explorer**auswählt, implementiert wird, um den Inhalt zu ändern, der im **Eigenschaften** Fenster angezeigt wird.  
  
1.  Das Objekt, das von einem VSPackage erstellt wird, das im ausgewählten Fenster positioniert ist, ruft <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> auf, um <xref:Microsoft.VisualStudio.Shell.Interop.STrackSelection> Aufruf <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection>haben.  
  
2.  Der Auswahlcontainer, vorausgesetzt, durch das ausgewählte Fenster erstellt ein eigenes <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>\-Objekt.  Wenn die Auswahl ändert, wird ein VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> an alle Listener in der Umgebung, einschließlich des **Eigenschaften** Fenster, die Änderung zu benachrichtigen.  Sie bietet auch Zugriff auf die Hierarchie und das Element, das der neuen Auswahl informationsbezogen ist.  
  
3.  Aufrufen von <xref:Microsoft.VisualStudio.Shell.Interop.ITrackSelection.OnSelectChange%2A> und Übergeben der ausgewählten Elemente in Hierarchien `VSHPROPID_BrowseObject`\-Parameter füllt das <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>\-Objekt auf.  
  
4.  Ein Objekt, das von [IDispatch Interface](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5) abgeleitet wird, ist für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> für das angeforderte Element zurückgegeben, und die Umgebung bindet es an ein <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> \(siehe nachfolgenden Schritt\).  Wenn der Aufruf fehlschlägt, wird die Umgebung `IVsHierarchy::GetProperty`einen zweiten Aufruf und übergibt ihn der Auswahlcontainer <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , den das Hierarchien oder \- Elemente festlegen.  
  
     Das Projekt ein VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nicht erstellt werden, da das Umgebung\-angegebene VSPackages Fenster, das sie implementiert \(z. B. **Projektmappen\-Explorer**\) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> für die Zwecke erstellt.  
  
5.  Die Umgebung ruft die Methoden von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> auf, um die Objekte auf Grundlage der `IDispatch`\-Schnittstelle abzurufen, um das **Eigenschaften** Fenster auszufüllen.  
  
 Wenn ein Wert im **Eigenschaften** Fenster geändert wird, VSPackages\-Werkzeug `IVsTrackSelectionEx::OnElementValueChangeEx` und `IVsTrackSelectionEx::OnSelectionChangeEx` , die Änderung des Elementwert.  Die Umgebung wird anschließend <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> oder <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> auf, um die Informationen im Fenster angezeigt **Eigenschaften** auszuführen, das mit den Eigenschaftswerten synchronisiert wird.  Weitere Informationen finden Sie unter [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](../../misc/updating-property-values-in-the-properties-window.md).  
  
 Neben der Auswahl eines anderen Projektelements in **Projektmappen\-Explorer** , um die Eigenschaften anzuzeigen, die für dieses Element verknüpft sind, können Sie ein anderes Objekt aus einem Formular oder einem Dokumentfenster auch mithilfe der Dropdownliste auswählen, die auf dem **Eigenschaften** Fenster verfügbar ist.  Weitere Informationen finden Sie unter [Liste der Eigenschaften im Fenster Objekt](../../extensibility/internals/properties-window-object-list.md).  
  
 Sie können ändern, wie Informationen im Raster aus alphabetischem **Eigenschaften** Fenster zu Kategoriem angezeigt werden, und falls verfügbar, können Sie eine Eigenschaftenseite für ein ausgewähltes Objekt auch öffnen, indem Sie auf die entsprechenden Schaltflächen im **Eigenschaften** Fenster klicken.  Weitere Informationen finden Sie unter [Eigenschaften\-Fenster\-Schaltflächen](../../extensibility/internals/properties-window-buttons.md) und [Eigenschaftenseiten](../../extensibility/internals/property-pages.md).  
  
 Schließlich enthält den unteren Rand des Fensters **Eigenschaften** auch eine Beschreibung des Felds, das im Fenster **Eigenschaften** Raster ausgewählt ist.  Weitere Informationen finden Sie unter [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](../../misc/getting-field-descriptions-from-the-properties-window.md).  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)