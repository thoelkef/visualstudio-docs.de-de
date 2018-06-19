---
title: Übersicht über Eigenschaftenfenster | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: e255795a52064723477eda4e1aca532adedb6be1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
ms.locfileid: "31131613"
---
# <a name="properties-window-overview"></a>Übersicht über Eigenschaftenfenster
Die **Eigenschaften** Fenster dient zum Anzeigen von Eigenschaften für Objekte, die ausgewählt werden, in der zwei Haupttypen von Windows zur Verfügung, in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Diese beiden Typen von Windows werden zu können:  
  
-   Toolfenster, z. B. den Projektmappen-Explorer und Klassenansicht, Objekt-browser  
  
-   Dokumentfenster mit solchen Editoren und Designern als der Forms-Designer, die XML-Editor und die HTML-editor  
  
## <a name="using-the-properties-window"></a>Das Fenster "Eigenschaften"  
 Die **Eigenschaften** Fenster zeigt die Eigenschaften der einzelnen oder mehreren gewählten Elementen. Wenn mehrere Elemente ausgewählt sind, wird die Schnittmenge aller Eigenschaften für alle ausgewählten Objekte angezeigt.  
  
 Ereignisse im Zusammenhang mit einem ausgewählten Objekt innerhalb einer Form Entwurfsfenster oder HTML-Editor mit COM+-Metadaten werden angezeigt, der **Eigenschaften** Fenster. Z. B. eine Schaltfläche auswählen und ihre zugeordneten Ereignissen, z. B. Anzeigen einer `OnClick` Ereignis, das mit dieser Schaltfläche verknüpft werden kann.  
  
 Ereignisse angezeigt, der **Eigenschaften** Fenster dienen in erster Linie mit Objekten, die in Code gebunden sind. Wenn Sie ein Dateiformat, die nichts mit Code tun nicht besitzt bearbeiten, sind Sie nicht vorhaben, um Ereignisse. Ereignisse werden nur angezeigt, der **Eigenschaften** Fenster, wenn eine Bindung zwischen der Ausführung von Code und bestimmte Ereignisse im Zusammenhang mit spezifischen Objekten vorhanden ist. Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt, das ausgeführt wird, wenn das Objekt aktiviert wird.  
  
 Die folgende Tabelle enthält die primären Schnittstellen, die von der **Eigenschaften** Fenster.  
  
|Schnittstellenname|Beschreibung|  
|--------------------|-----------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Enthält eine Liste der Kategorien auf die **Eigenschaften** Fenster und ordnet jede Eigenschaft eine Kategorie.|  
|[IDispatch-Schnittstelle](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)|Macht Methoden und Eigenschaften für die Programmierung von Tools und andere Anwendungen, die Unterstützung der Automatisierung des Objekts.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Schaltflächen mit den Auslassungszeichen (...) bietet *Generatoren* , mit denen modalen Dialogfeldern, die durch das Objekt selbst implementiert geöffnet. Verwendet, wenn ein Wert vom Benutzer in einem Textfeld einfach nicht typisiert ist. Beispielsweise kann verwendet werden, um ein Farbauswahl zu öffnen, die den RGB-Wert für Sie bestimmt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Bietet Zugriff auf Objekte, die zum Aktualisieren der angezeigten Informationen auf der **Eigenschaften** Fenster. <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster implementiert, auswählbare Objekte mit verwandten Eigenschaften angezeigt werden, enthält.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Bietet Informationen über den Typ eines Objekts, z. B. Methoden einer Schnittstelle und die Felder einer Struktur an.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Ermöglicht VSPackages Auswahl Ereignisse benachrichtigt werden soll und zum Abrufen von Informationen zu den aktuellen Projekthierarchie, Element Elementwert und Benutzeroberflächenkontext Befehl.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt die Umgebung mit Zugriff auf mehrere Auswahlmöglichkeiten bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Zur Bereitstellung von lokalisierter Namen für einige Eigenschaften angezeigt, der **Eigenschaften** Fenster.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Benachrichtigt die registrierten VSPackages von Änderungen an der aktuellen Auswahl, Wert des Elements oder Befehl Benutzeroberflächenkontext.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Informiert die Umgebung eine Änderung in der aktuellen Auswahl, und ermöglicht den Zugriff auf die Hierarchie und Element-Informationen im Zusammenhang mit der die neue Auswahl.|  
  
 Weitere Informationen zu `IDispatch`, finden Sie in der MSDN Library.  
  
## <a name="see-also"></a>Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)   
 [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)