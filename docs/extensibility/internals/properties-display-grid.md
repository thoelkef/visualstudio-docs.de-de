---
title: Eigenschaften-Anzeigeraster | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- properties [Visual Studio SDK], grid
ms.assetid: 318e41b0-acf5-4842-b85e-421c9d5927c5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d094c32ba8a64fc636f3fb6dfb2944dc3955628a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706188"
---
# <a name="properties-display-grid"></a>Eigenschaften-Anzeigeraster

Im Fenster **Eigenschaften** werden Felder innerhalb eines Rasters angezeigt. Die linke Spalte enthält die Eigenschaftennamen. die rechte Spalte enthält die Eigenschaftswerte.

## <a name="work-with-the-grid"></a>Arbeiten mit dem Raster

Die zweispaltige Liste zeigt konfigurationsunabhängige Eigenschaften, die zur Entwurfszeit geändert werden können, und ihre aktuellen Einstellungen. Beachten Sie, dass möglicherweise nicht alle Eigenschaften angezeigt werden. Eine Eigenschaft kann als ausgeblendet festgelegt werden, z. B. durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> Methode. Zum Ausblenden von Eigenschaften mit untergeordneten Eigenschaften:

1. Legen `pfDisplay` Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.DisplayChildProperties%2A> den `FALSE`Parameter in fest.

2. Legen `pfHide` Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HideProperty%2A> den `TRUE`Parameter in fest.

Um Informationen in das **Eigenschaftenfenster** <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>zu übertragen, verwendet die IDE . <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>wird von VSPackages für jedes Fenster aufgerufen, das wählbare Objekte mit zugehörigen Eigenschaften enthält, die im **Eigenschaftenfenster** angezeigt werden sollen. Implementierung von Aufrufen `GetProperty` <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> im **Projektmappen-Explorer**mithilfe von [__VSHPROPID. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>) in der Projekthierarchie, um die ausserbaren Objekte in der Hierarchie zu erwerben.

Wenn Ihr VSPackage __VSHPROPID nicht [unterstützt. VSHPROPID_BrowseObject](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_BrowseObject>)versucht die IDE, den Wert für __VSHPROPID zu <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetProperty%2A> [verwenden. VSHPROPID_SelContainer,](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID.VSHPROPID_SelContainer>) die das Hierarchieelement oder die Artikel bereitstellen.

Ihr Projekt VSPackage muss <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> nicht erstellt werden, da das von IDE bereitgestellte Fensterpaket, das es implementiert (z. B. **Projektmappen-Explorer**), <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> in seinem Namen erstellt wird.

<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>besteht aus drei Methoden, die von der IDE aufgerufen werden:

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.CountObjects%2A>enthält die Anzahl der Objekte, die im **Eigenschaftenfenster** angezeigt werden sollen.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A>gibt `IDispatch` die Objekte zurück, die ausgewählt sind, um im **Eigenschaftenfenster** angezeigt zu werden.

- <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.SelectObjects%2A>ermöglicht es, dass alle von <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> ihm zurückgegebenen Objekte vom Benutzer ausgewählt werden. Dadurch kann das VSPackage die Auswahl, die dem Benutzer in der Benutzeroberfläche angezeigt wird, visuell aktualisieren.

Das **Fenster Eigenschaften** extrahiert `IDispatch` Informationen aus den Objekten, um die durchsuchten Eigenschaften abzurufen. Der Eigenschaftenbrowser `IDispatch` verwendet, um das Objekt zu `ITypeInfo`fragen, welche `IDispatch::GetTypeInfo`Eigenschaften es unterstützt, indem er abfragt, das von abgerufen wird. Der Browser verwendet diese Werte dann, um das **Eigenschaftenfenster** aufzufüllen und die Werte für einzelne Eigenschaften zu ändern, die im Raster angezeigt werden. Die Eigenschafteninformationen werden innerhalb des Objekts selbst verwaltet.

Da die zurückgegebenen Objekte unterstützen, `IDispatch`kann der Aufrufer Informationen wie `IDispatch::Invoke` `ITypeInfo::Invoke` den Namen des Objekts abrufen, indem er entweder oder mit einem vordefinierten Dispatch-ID (DISPID) aufruft, der die gewünschten Informationen darstellt. Deklarierte DISPIDs sind negativ, um sicherzustellen, dass sie nicht mit benutzerdefinierten Bezeichnern in Konflikt stehen.

Im Fenster **Eigenschaften** werden je nach den Attributen bestimmter Eigenschaften eines ausgewählten Objekts verschiedene Arten von Feldern angezeigt. Zu diesen Feldern gehören Bearbeitungsfelder, Dropdownlisten und Links zu benutzerdefinierten Editor-Dialogfeldern.

- Werte, die in einer aufgezählten <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer.GetObjects%2A> Liste `IDispatch`enthalten sind, werden von einer Abfrage an abgerufen. Werte, die aus einer aufgezählten Liste abgerufen werden, können im Eigenschaftenraster durch Doppelklicken auf den Feldnamen oder durch Klicken auf den Wert und Auswählen des neuen Werts aus der Dropdownliste geändert werden. Für Eigenschaften, die über vordefinierte Einstellungen aus aufgezählten Listen verfügen, doppelklicken Sie in der Eigenschaftenliste auf den Eigenschaftennamen, indem Sie auf die verfügbaren Optionen klicken. Doppelklicken Sie bei vordefinierten Eigenschaften mit nur zwei Optionen, z. B. true/false, auf den Eigenschaftsnamen, um zwischen den Auswahlmöglichkeiten zu wechseln.

- Wenn <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.HasDefaultValue%2A> `false`dies der Option ist, wird der Wert in fett formatiert angezeigt, was darauf hinweist, dass der Wert geändert wurde. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing.CanResetPropertyValue%2A>wird verwendet, um zu bestimmen, ob der Wert auf den ursprünglichen Wert zurückgesetzt werden kann. Wenn dies der Vorgang der Option ist, können Sie wieder zur Standardeinstellung wechseln, indem Sie mit der rechten Maustaste auf den Wert klicken und im angezeigten Menü **"Zurücksetzen"** auswählen. Andernfalls müssen Sie den Wert manuell wieder auf den Standardwert ändern. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Außerdem können Sie die Namen der während der Entwurfszeit angezeigten Eigenschaften lokalisieren und ausblenden, wirken sich jedoch nicht auf die Eigenschaftennamen aus, die während der Laufzeit angezeigt werden.

- Wenn Sie auf die Schaltfläche Auslassungspunkte (...) klicken, wird eine Liste der Eigenschaftswerte angezeigt, aus denen der Benutzer auswählen kann (z. B. eine Farbauswahl oder eine Schriftartliste). <xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>stellt diese Werte bereit.

## <a name="see-also"></a>Weitere Informationen

- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
