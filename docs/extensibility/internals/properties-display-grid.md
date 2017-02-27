---
title: "Raster von Eigenschaften anzeigen | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaften [Visual Studio SDK], Raster"
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Raster von Eigenschaften anzeigen
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die **Eigenschaften** Fenster Felder in einem Raster angezeigt.  Die linke Spalte enthält die Eigenschaftennamen. die rechte Spalte enthält die Eigenschaftswerte.  
  
## Mit dem Datenblatt bearbeiten  
 Die Zwei COLUMN\-Liste wird konfigurationsunabhängige Eigenschaften, die zur Entwurfszeit geändert werden können, und ihre aktuellen Einstellungen an.  Beachten Sie, dass alle Eigenschaften möglicherweise nicht angezeigt würden.  Eine Eigenschaft kann festgelegt werden, wie ausgeblendet werden, z. B. durch Festlegen der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A>\-Methode implementiert.  Insbesondere Eigenschaften mit untergeordneten Eigenschaften ausblenden können, finden [Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften](../../misc/hiding-properties-that-have-child-properties.md).  
  
 Um Informationen zum **Eigenschaften** Fenster zu drücken, wird die IDE <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für alle Fenster aufgerufen, das auswählbare Objekte mit den zugehörigen enthält **Eigenschaften** im Fenster Eigenschaften angezeigt.  Die Implementierung der Projektmappen\-Explorer aus <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> ruft `GetProperty` mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> in der Projekthierarchie auf, um die browsebaren Objekte in der Hierarchie abzurufen.  
  
 Wenn ein VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>nicht unterstützt, versucht die IDE, <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> unter Verwendung des Werts für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> zu verwenden, das die Hierarchien oder \- Elemente festlegen.  
  
 Das Projekt muss keine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> VSPackages zu erstellen, da die IDE\-angegebene Sichtverpackung, die er implementiert \(z. B. **Projektmappen\-Explorer**\) <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> für die Zwecke erstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> besteht aus drei Methoden, die von der IDE aufgerufen werden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> enthält die Anzahl der Objekte, die ausgewählt werden, im **Eigenschaften** Fenster angezeigt werden soll.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> gibt die `IDispatch`\-Objekten zurück, die dieser Option werden im **Eigenschaften** Fenster angezeigt werden soll.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> ermöglicht es für alle Objekte, die von zurückgegebenen <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vom Benutzer ausgewählt werden sollen.  Dadurch kann ein VSPackage, um die Auswahl visuell zu aktualisieren, die dem Benutzer in der Benutzeroberfläche angezeigt wird.  
  
 Das Fenster **Eigenschaften** extrahiert Informationen aus den `IDispatch`\-Objekten, um den Eigenschaften zu erhalten, die durchsucht werden.  Der Eigenschaftenbrowser `IDispatch` verwendet, um das Objekt zu fragen, welche Eigenschaften es unterstützt, indem `ITypeInfo`abfragt, das von `IDispatch::GetTypeInfo`abgerufen wird.  Der Browser verwendet dann diese Werte, um das Fenster **Eigenschaften** gefüllt und die Werte für die einzelnen Eigenschaften zu ändern, die im Datenblatt angezeigt werden.  Die Eigenschafteninformationen werden innerhalb des Objekts selbst beibehalten.  
  
 Da die zurückgegebenen Objekte `IDispatch`unterstützen, kann der Aufrufer erhalten Informationen wie der Name des Objekts, indem er entweder `IDispatch::Invoke` oder `ITypeInfo::Invoke` mit einem vordefinierten Dispatchbezeichner \(DISPID\) aufruft, der die gewünschten Informationen darstellt.  Deklariertes DISPID ist negativ, um sicherzustellen, dass sie nicht mit benutzerdefinierten Bezeichnern Konflikt auftritt.  
  
 Das **Eigenschaften** Fenster zeigt verschiedene Typen von Feldern je nach Attributen bestimmter Eigenschaften eines ausgewählten Objekts an.  Diese Felder werden Eingabefelder, Dropdownlisten und Links zu den Dialogfeldern benutzerdefinierten Editor.  
  
-   Die Werte, die in einer Aufzählungsliste enthalten sind, werden durch eine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>\-Abfrage zu `IDispatch`abgerufen.  abgerufene Werte aus einer Aufzählungsliste können im Eigenschaftenraster bearbeitet werden, indem Sie auf den Feldnamen doppelklickten, oder indem Sie auf den Wert klicken und den neuen Wert aus der Dropdownliste ausgewählt haben.  Für Eigenschaften, die Einstellungen aus den Aufzählungslisten vordefiniert sind, auf den Eigenschaftennamen in den listgängen Eigenschaftenlisten über die verfügbaren Optionen doppelklicken.  Für vordefinierte Eigenschaften mit nur zwei Optionen, z. B. true oder false, doppelklicken Sie auf den Namen, um zwischen der Auswahl umzuschalten.  
  
-   Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A>`false`ist. Er gibt an, dass der Wert geändert wurde, wird der Wert in fett formatiertem Text angezeigt.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> wird verwendet, um zu ermitteln, ob der Wert in den ursprünglichen Wert zurückgesetzt werden kann.  In diesem Fall können Sie an den Standardwert ändern, indem Sie auf den Wert mit der rechten Maustaste darauf klicken und **Zurücksetzen** im angezeigten Menü auswählen.  Andernfalls müssen Sie den Wert für den standardmäßigen manuell ändern.  <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> können Sie auch die Namen von Eigenschaften zu suchen und zu verbergen, die während der Entwurfszeit angezeigt werden, doch hat keine Auswirkungen auf die Eigenschaftennamen, die während der Laufzeit angezeigt werden.  
  
-   Durch Klicken auf die Schaltfläche mit den Auslassungspunkten \(...\) zeigt eine Liste von Eigenschaftswerten an, aus der der Benutzer auswählen kann \(z. B. eine Liste Schriftart oder Farben\-Auswahl\-\).  <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> stellt diese Werte.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)