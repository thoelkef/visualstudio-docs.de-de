---
title: Eigenschaften anzeigen Raster | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 35b36c357c9b98d81627eea0d511b0b4fd49f693
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="properties-display-grid"></a>Raster von Eigenschaften anzeigen
Die **Eigenschaften** Fenster werden Felder in einem Raster angezeigt. Die linke Spalte enthält die Eigenschaftennamen. die rechte Spalte enthält die Eigenschaftswerte an.  
  
## <a name="working-with-the-grid"></a>Arbeiten mit dem Raster  
 Die zweispaltige Liste zeigt konfigurationsunabhängigen Eigenschaften, die zur Entwurfszeit und ihren aktuellen Einstellungen geändert werden können. Beachten Sie, dass alle Eigenschaften nicht angezeigt werden können. Eine Eigenschaft kann festgelegt werden als ausgeblendet, z. B. durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> Methode. Insbesondere zum Ausblenden von Eigenschaften, die untergeordneten Eigenschaften:  
  
1.  Legen Sie die `pfDisplay` im Parameters <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> auf `FALSE`.  
  
2.  Legen Sie die `pfHide` im Parameters <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> auf `TRUE`.  
  
 Push-Informationen zu den **Eigenschaften** Fenster die IDE verwendet <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>wird von VSPackages aufgerufen, für jedes Fenster, die auswählbare Objekte mit verwandten Eigenschaften anzuzeigenden enthält die **Eigenschaften** Fenster. **Projektmappen-Explorer**der Implementierung von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> Aufrufe `GetProperty` mit <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> in der Projekthierarchie durchsuchbare Objekte in der Hierarchie zu erhalten.  
  
 Wenn Ihr VSPackage nicht unterstützt <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID>, versucht die IDE verwenden <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> mithilfe des Werts für <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID> , dass die Hierarchieelement oder Elemente angeben.  
  
 Das Projekt, das VSPackage nicht erstellen muss <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> , da das Paket bereitgestellten IDE-Fenster, in dem sie implementiert (z. B. **Projektmappen-Explorer**) erstellt <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in dessen Auftrag aufzubauen.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>besteht aus drei Methoden, die von der IDE aufgerufen werden:  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>enthält die Anzahl der anzuzeigenden ausgewählten Objekte die **Eigenschaften** Fenster.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>Gibt die `IDispatch` anzuzeigenden ausgewählten Objekte die **Eigenschaften** Fenster.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>ermöglicht es einer der vom zurückgegebenen Objekte <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> vom Benutzer ausgewählt werden. Dadurch wird das VSPackage, um die Auswahl, die dem Benutzer in der Benutzeroberfläche angezeigten visuell zu aktualisieren.  
  
 Die **Eigenschaften** Fenster extrahiert Informationen aus der `IDispatch` Objekte zum Abrufen der Eigenschaften, die durchsucht wird. Eigenschaftenbrowser verwendet `IDispatch` , Fragen Sie dem Objekt Eigenschaften unterstützt, indem Sie Abfragen `ITypeInfo`, erhalten Sie von `IDispatch::GetTypeInfo`. Der Browser verwendet dann diese Werte zum Auffüllen der **Eigenschaften** Fenster und ändern Sie die Werte für die einzelnen Eigenschaften im Raster angezeigt. Die Eigenschafteninformationen werden innerhalb des Objekts selbst verwaltet.  
  
 Da die zurückgegebenen Objekte unterstützen `IDispatch`, der Aufrufer kann Informationen wie den Namen des Objekts abzurufen, durch den Aufruf eines `IDispatch::Invoke` oder `ITypeInfo::Invoke` mit einem vordefinierten Dispatch-ID (DISPID), die die gewünschte Informationen darstellt. Deklarierte DISPIDs sind negativ ist, um sicherzustellen, dass sie nicht mit benutzerdefinierten Bezeichnern in Konflikt stehen.  
  
 Die **Eigenschaften** Fenster werden verschiedene Typen von Feldern, die Abhängigkeit von den Attributen der bestimmte Eigenschaften eines ausgewählten Objekts angezeigt. Diese Felder umfassen Bearbeitungsfelder, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern.  
  
-   In einer nummerierten Liste enthaltenen Werte werden abgerufen, indem eine <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Abfragen zum `IDispatch`. Vom eine Aufzählungsliste abgerufene Werte können im Eigenschaftenraster geändert werden, auf den Feldnamen doppelklicken oder indem Sie auf den Wert und den neuen Wert aus der Dropdown-Liste auswählen. Für Eigenschaften, die Einstellungen von aufgezählten Listen vordefinierte verfügen, durchläuft die verfügbaren Auswahlmöglichkeiten Doppelklicken auf den Eigenschaftennamen in der Eigenschaftenliste. Doppelklicken Sie für vordefinierte Eigenschaften mit nur zwei Optionen, wie beispielsweise "true" / "false" auf den Namen der Eigenschaft, um zwischen den Optionen wechseln.  
  
-   Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> ist `false`, gibt an, dass der Wert geändert wurde, wird der Wert in Fettdruck angezeigt. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>wird verwendet, um festzustellen, ob der Wert auf den ursprünglichen Wert zurückgesetzt werden kann. Wenn also Sie wieder auf den Standardwert ändern können, indem Sie mit der rechten Maustaste des Werts und **zurücksetzen** aus dem Menü angezeigt. Andernfalls müssen Sie den Wert manuell wieder auf den Standardwert zu ändern. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Außerdem können Sie mit dem lokalisieren und blenden die Namen von Eigenschaften, die während der Entwurfszeit angezeigt, jedoch wirkt sich nicht auf die Eigenschaftennamen, die während der Laufzeit angezeigt.  
  
-   Klicken auf die Schaltfläche mit den Auslassungspunkten (...) zeigt eine Liste der Eigenschaftenwerte aus denen der Benutzer (z. B. eine Farbauswahl oder Schriftartenliste) auswählen kann. <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>Diese Werte werden bereitgestellt.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)