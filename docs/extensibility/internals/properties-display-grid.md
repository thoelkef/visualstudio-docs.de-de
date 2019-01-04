---
title: Eigenschaften anzeigen Raster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 26dfbf505229ef3994f91e6f4af5eaf56b4d0d2a
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53949562"
---
# <a name="properties-display-grid"></a>Anzeigeraster für Eigenschaften
Die **Eigenschaften** Fenster werden die Felder in einem Raster angezeigt. Die linke Spalte enthält die Eigenschaftennamen; die rechte Spalte enthält die Eigenschaftswerte an.  
  
## <a name="working-with-the-grid"></a>Arbeiten mit dem Raster  
 Die Liste zwei Spalten zeigt konfigurationsunabhängige Eigenschaften, die zur Entwurfszeit und ihre aktuellen Einstellungen geändert werden können. Beachten Sie, dass alle Eigenschaften nicht angezeigt werden können. Eine Eigenschaft kann festgelegt werden als ausgeblendet, z. B. durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> Methode. Insbesondere auf Ausblenden-Eigenschaften, die untergeordneten Eigenschaften:  
  
1. Legen Sie die `pfDisplay` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> zu `FALSE`.  
  
2. Legen Sie die `pfHide` Parameter im <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> zu `TRUE`.  
  
   Push-Informationen zu den **Eigenschaften** Fenster die IDE verwendet <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster mit auswählbaren Objekte mit verwandten Eigenschaften, die in angezeigt werden aufgerufen, die **Eigenschaften** Fenster. **Projektmappen-Explorer**Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Aufrufe `GetProperty` mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> in der Projekthierarchie zum Abrufen dem durchsuchbare Objekte in der Hierarchie.  
  
   Wenn das VSPackage nicht unterstützt <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, versucht die IDE verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> mithilfe des Werts für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , dass das Hierarchieelement oder die Elemente angeben.  
  
   Das Projekt, das VSPackage nicht erstellen muss <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , da das Paket bereitgestellten IDE-Fenster, in dem sie implementiert (z. B. **Projektmappen-Explorer**) erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in dessen Auftrag aufzubauen.  
  
   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> besteht aus drei Methoden, die von der IDE aufgerufen werden:  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A> enthält die Anzahl der Objekte, die in angezeigt werden sollen die **Eigenschaften** Fenster.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Gibt die `IDispatch` Objekte, die in angezeigt werden sollen die **Eigenschaften** Fenster.  
  
- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A> ermöglicht es eines der Objekte, die vom <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vom Benutzer ausgewählt werden. Dadurch wird das VSPackage, um die Auswahl, die dem Benutzer in der Benutzeroberfläche angezeigten visuell zu aktualisieren.  
  
  Die **Eigenschaften** Fenster extrahiert Informationen aus der `IDispatch` Objekte zum Abrufen der Eigenschaften, die durchsucht werden. Verwendet den Eigenschaftenbrowser `IDispatch` , bitten Sie dem Objekt Eigenschaften unterstützt durch Abfragen `ITypeInfo`, erhalten Sie vom `IDispatch::GetTypeInfo`. Der Browser verwendet dann diese Werte zum Auffüllen der **Eigenschaften** Fenster und ändern Sie die Werte für die einzelnen Eigenschaften, die im Raster angezeigt. Die Informationen zu den Ausführungseigenschaften wird innerhalb des Objekts selbst verwaltet.  
  
  Da die zurückgegebenen Objekte unterstützen `IDispatch`, der Aufrufer erhalten Informationen wie z. B. den Namen des Objekts durch Aufrufen von entweder `IDispatch::Invoke` oder `ITypeInfo::Invoke` mit einer vordefinierten Dispatch-ID (DISPID), die die gewünschte Informationen darstellt. Deklarierte DISPIDs ist negativ, um sicherzustellen, dass sie nicht mit den benutzerdefinierten Bezeichnern in Konflikt stehen.  
  
  Die **Eigenschaften** verschiedene Typen von Feldern, die Abhängigkeit von den Attributen der bestimmte Eigenschaften eines ausgewählten Objekts angezeigt. Diese Felder umfassen Bearbeitungsfelder, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern.  
  
- In der eine Aufzählungsliste enthaltenen Werte werden abgerufen, indem eine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> nach Abfragen `IDispatch`. Werte aus einer nummerierten Liste können durch Doppelklicken auf den Namen des Felds oder durch Klicken auf den Wert ein, und wählen den neuen Wert aus der Dropdown-Liste im Eigenschaftenraster geändert werden. Bei Eigenschaften, die Einstellungen aus Aufzählungslisten vordefinierte verfügen, durchläuft die verfügbaren Optionen durch Doppelklicken auf den Eigenschaftennamen in der Eigenschaftenliste. Doppelklicken Sie für vordefinierte Eigenschaften mit nur zwei Auswahlmöglichkeiten gibt, wie z. B. wahr/falsch auf den Namen der Eigenschaft, um zwischen den Optionen wechseln.  
  
- Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> ist `false`, gibt an, dass der Wert geändert wurde, der Wert wird in Fettdruck angezeigt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A> wird verwendet, um festzustellen, ob der Wert auf den ursprünglichen Wert zurückgesetzt werden kann. Wenn also, Sie wieder auf den Standardwert ändern können, indem mit der rechten Maustaste in des Werts und **zurücksetzen** im Menü angezeigt. Andernfalls müssen Sie den Wert manuell wieder auf den Standardwert zu ändern. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> ermöglicht auch lokalisieren und blenden die Namen der Eigenschaften, die während der Entwurfszeit angezeigt, jedoch wirkt sich nicht auf die Eigenschaftennamen, die während der Laufzeit angezeigt.  
  
- Klicken auf die Schaltfläche mit den Auslassungspunkten (...) zeigt eine Liste der Eigenschaftswerte, die in denen der Benutzer (z. B. eine Farbauswahl angezeigt oder Schriftartenliste) auswählen kann. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder> Diese Werte bereitgestellt werden.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)