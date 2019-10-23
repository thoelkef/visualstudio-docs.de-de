---
title: Übersicht über das Eigenschaften Fenster | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 61887844e06a88cab9eaa8ca8be7a89c124e2340
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72725084"
---
# <a name="properties-window-overview"></a>Übersicht über Eigenschaftenfenster
Das Fenster **Eigenschaften** wird zum Anzeigen von Eigenschaften für Objekte verwendet, die in den beiden Haupttypen von Fenstern ausgewählt sind, die in der integrierten Entwicklungsumgebung (IDE) von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügbar sind. Diese beiden Windows-Typen sind:

- Tool Fenster, z. b. Projektmappen-Explorer, Klassenansicht und Objektkatalog

- Dokument Fenster, die Editoren und Designer als den Formular-Designer, den XML-Editor und den HTML-Editor enthalten

## <a name="using-the-properties-window"></a>Verwenden des Fensters "Eigenschaften"
 Das Fenster **Eigenschaften** zeigt die Eigenschaften von einzelnen oder mehreren ausgewählten Elementen an. Wenn mehrere Elemente ausgewählt sind, wird die Schnittmenge aller Eigenschaften für alle ausgewählten Objekte angezeigt.

 Im **Eigenschaften** Fenster werden Ereignisse angezeigt, die sich auf ein ausgewähltes Objekt innerhalb eines Formular Entwurfs Fensters oder HTML-Editor mit com+-Metadaten beziehen. Beispielsweise können Sie eine Schaltfläche auswählen und die zugehörigen Ereignisse anzeigen, z. b. ein `OnClick` Ereignis, das mit dieser Schaltfläche verknüpft werden kann.

 Ereignisse, die im **Eigenschaften** Fenster angezeigt werden, werden hauptsächlich mit Objekten verwendet, die an Code gebunden sind. Wenn Sie ein Dateiformat bearbeiten, das nicht mit Code zu tun hat, sind keine Ereignisse vorhanden. Ereignisse werden nur im **Eigenschaften** Fenster angezeigt, wenn eine Bindung zwischen ausgelaufendem Code und bestimmten Ereignissen besteht, die bestimmten Objekten zugeordnet sind. Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt, das ausgeführt wird, wenn dieses Objekt aktiviert wird.

 In der folgenden Tabelle werden die primären Schnittstellen aufgelistet, die im Fenster **Eigenschaften** verwendet werden.

|Schnittstellen Name|Beschreibung|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Stellt eine Liste von Kategorien für das **Eigenschaften** Fenster bereit und ordnet jede Eigenschaft einer Kategorie zu.|
|[IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Macht die Methoden und Eigenschaften eines Objekts für Programmier Tools und andere Anwendungen verfügbar, die Automation unterstützen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Bietet Schaltflächen mit Auslassungs Zeichen (... *), die* als Generatoren bezeichnet werden. Wird verwendet, wenn ein Wert nicht einfach vom Benutzer in einem Textfeld eingegeben wird. Beispielsweise kann Sie verwendet werden, um eine Farbauswahl zu öffnen, die den RGB-Wert bestimmt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Bietet Zugriff auf Objekte, die zum Aktualisieren von Informationen verwendet werden, die im **Eigenschaften** Fenster angezeigt werden. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster implementiert, das auswählbare Objekte mit zugehörigen Eigenschaften enthält, die angezeigt werden sollen.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bietet Informationen zum Typ eines Objekts, z. b. Methoden einer Schnittstelle und Felder einer Struktur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Ermöglicht VSPackages das Empfangen von Benachrichtigungen über Auswahl Ereignisse und das Abrufen von Informationen über die aktuelle Projekt Hierarchie, das Element, den Elementwert und den Befehls Benutzeroberflächen Kontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt der Umgebung Zugriff auf Mehrfachauswahl zur Verfügung.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Wird verwendet, um lokalisierte Namen für einige Eigenschaften bereitzustellen, die im **Eigenschaften** Fenster angezeigt werden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Benachrichtigt registrierte VSPackages über Änderungen an der aktuellen Auswahl, dem Elementwert oder dem Befehls Benutzeroberflächen Kontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Benachrichtigt die Umgebung über eine Änderung in der aktuellen Auswahl und ermöglicht den Zugriff auf Hierarchie-und Element Informationen im Zusammenhang mit der neuen Auswahl.|

 Weitere Informationen zu `IDispatch` finden Sie in der MSDN Library.

## <a name="see-also"></a>Siehe auch
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
- [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)