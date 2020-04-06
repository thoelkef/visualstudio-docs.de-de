---
title: Eigenschaftenfenster Übersicht | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 445a43cec976f363873c89dfe9b8e05429aebaf2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706034"
---
# <a name="properties-window-overview"></a>Übersicht über Eigenschaftenfenster
Das **Fenster Eigenschaften** wird verwendet, um Eigenschaften für Objekte anzuzeigen, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die in den beiden Hauptfenstertypen ausgewählt wurden, die in der integrierten Entwicklungsumgebung (IDE) verfügbar sind. Diese beiden Arten von Fenstern sind:

- Toolfenster wie Projektmappen-Explorer, Klassenansicht und Objektbrowser

- Dokumentfenster mit Editoren und Designern wie Formular-Designer, XML-Editor und HTML-Editor

## <a name="using-the-properties-window"></a>Verwenden des Eigenschaftenfensters
 Im **Fenster Eigenschaften** werden die Eigenschaften einzelner oder mehrerer ausgewählter Elemente angezeigt. Wenn mehrere Elemente ausgewählt sind, wird der Schnittpunkt aller Eigenschaften für alle ausgewählten Objekte angezeigt.

 Ereignisse, die sich auf ein ausgewähltes Objekt in einem Formularentwurfsfenster oder HTML-Editor mit COM+-Metadaten beziehen, werden im **Eigenschaftenfenster** angezeigt. Sie können z. B. eine Schaltfläche auswählen und `OnClick` die zugehörigen Ereignisse anzeigen, z. B. ein Ereignis, das mit dieser Schaltfläche verknüpft werden kann.

 Ereignisse, die im **Eigenschaftenfenster** angezeigt werden, werden hauptsächlich mit Objekten verwendet, die an Code gebunden sind. Wenn Sie ein Dateiformat bearbeiten, das nichts mit Code zu tun hat, werden Sie keine Ereignisse haben. Ereignisse werden nur im **Eigenschaftenfenster** angezeigt, wenn eine Bindung zwischen ausgeführtem Code und bestimmten Ereignissen besteht, die bestimmten Objekten zugeordnet sind. Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt, das ausgeführt wird, wenn dieses Objekt aktiviert wird.

 In der folgenden Tabelle sind die primären Schnittstellen aufgeführt, die vom **Eigenschaftenfenster** verwendet werden.

|Schnittstellenname|BESCHREIBUNG|
|--------------------|-----------------|
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Stellt eine Liste von Kategorien für das **Eigenschaftenfenster** bereit und ordnet jede Eigenschaft einer Kategorie zu.|
|[IDispatch-Schnittstelle](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)|Stellt die Methoden und Eigenschaften eines Objekts für Programmiertools und andere Anwendungen bereit, die die Automatisierung unterstützen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Stellt Auslassungsschaltflächen (...) bereit, die als *Builder* bezeichnet werden und modale Dialogfenster öffnen, die vom Objekt selbst implementiert werden. Wird verwendet, wenn ein Wert vom Benutzer nicht einfach in ein Textfeld eingegeben werden kann. Sie kann z. B. zum Öffnen einer Farbauswahl verwendet werden, die den RGB-Wert für Sie bestimmt.|
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Bietet Zugriff auf Objekte, die zum Aktualisieren von Informationen verwendet werden, die im **Eigenschaftenfenster** angezeigt werden. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>wird von VSPackages für jedes Fenster implementiert, das wählbare Objekte mit zugehörigen Eigenschaften enthält, die angezeigt werden sollen.|
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Enthält Informationen zum Typ eines Objekts, z. B. Methoden einer Schnittstelle und Felder einer Struktur.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Ermöglicht VSPackages, Benachrichtigungen über Auswahlereignisse zu empfangen und Informationen über die aktuelle Projekthierarchie, den Elementwert, den Elementwert und den Benutzeroberflächenkontext abzurufen.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt die Umgebung mit Zugriff auf die Mehrfachauswahl bereit.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Wird verwendet, um lokalisierte Namen für einige Eigenschaften bereitzustellen, die im **Eigenschaftenfenster** angezeigt werden.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Benachrichtigt registrierte VSPackages über Änderungen an der aktuellen Auswahl, am Elementwert oder am Befehlsbenutzeroberflächenkontext.|
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Benachrichtigt die Umgebung über eine Änderung in der aktuellen Auswahl und bietet Zugriff auf die Hierarchie- und Elementinformationen in Bezug auf die neue Auswahl.|

 Weitere Informationen `IDispatch`zu finden Sie in der MSDN-Bibliothek.

## <a name="see-also"></a>Weitere Informationen
- [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)
- [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)
