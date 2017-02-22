---
title: "&#220;bersicht &#252;ber Eigenschaftenfenster | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Eigenschaftenfenster"
ms.assetid: 289ed4f2-02ac-4899-855e-42dfe57ee05f
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# &#220;bersicht &#252;ber Eigenschaftenfenster
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Das **Eigenschaften** Fenster wird verwendet, um Eigenschaften für die Objekte anzuzeigen, die in den beiden wichtigsten Arten von Fenstern aktiviert werden, die in der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) verfügbar sind.  Diese beiden Typen von Windows sind:  
  
-   Toolfenster Klassenansicht und der Objektkatalog, wie der Projektmappen\-Explorer  
  
-   Dokumentfenster, die solche Editoren und Designern wie der Formular\-Designer, XML\-Editor und HTML\-Editor enthalten  
  
## Verwenden des Eigenschaftenfensters  
 Das Fenster wird **Eigenschaften** die Eigenschaften einzelner oder mehrere ausgewählte Elemente an.  Wenn mehrere Elemente ausgewählt sind, wird die Schnittmenge aller Eigenschaften für alle ausgewählten Objekte angezeigt.  
  
 Die Ereignisse, die an einem ausgewählten Objekt in einem Formular entwurf Fensters oder eines HTML\-Editors mit COM\+\-Metadaten verknüpft sind, werden im **Eigenschaften** Fenster angezeigt.  Beispielsweise können Sie eine Schaltfläche auswählen und ihre zugeordneten Ereignisse, z. B. ein `OnClick`\-Ereignis an, das dieser Schaltfläche verknüpft werden kann.  
  
 Die Ereignisse, die im **Eigenschaften** Fenster angezeigt werden, werden hauptsächlich mit Objekten verwendet, die dem Code gebunden werden.  Wenn Sie ein Dateiformat bearbeiten, das keine Auswirkungen hat, mit Code zu Fall werden keine Ereignisse verfügen.  Ereignisse werden nur im **Eigenschaften** Fenster angezeigt, wenn es sich um eine Bindung zwischen dem Ausführen von Code sowie bestimmte Ereignisse vorhanden sind, die mit bestimmten Objekten zugeordnet sind.  Ein Beispiel hierfür wäre Code hinter einem ausgewählten Objekt handeln, das ausgeführt wird, wenn dieses Objekt aktiviert ist.  
  
 In der folgenden Tabelle sind die primären Schnittstellen aufgeführt, die vom **Eigenschaften** Fenster verwendet werden.  
  
|Schnittstellen\-Name|Beschreibung|  
|--------------------------|------------------|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ICategorizeProperties>|Stellt eine Liste von Kategorien auf den **Eigenschaften** Fenster bereit und ordnet jede Eigenschaft mit einer Kategorie zu.|  
|[IDispatch\-Schnittstelle](http://msdn.microsoft.com/de-de/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)|Setzt die Methoden und Eigenschaften eines Objekts Programmierwerkzeuge und anderen Anwendungen aus, die Automatisierung unterstützen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IProvidePropertyBuilder>|Stellt die Schaltflächen mit den Auslassungspunkten \(...\) bereit, die *Generatoren* aufgerufen werden, die geöffnete Fenster des modalen Dialogfelds durch das Objekt selbst implementiert haben.  Wird verwendet, wenn ein Wert nicht leicht vom Benutzer in einem Textfeld eingegeben wird.  Beispielsweise würde er verwendet werden, um eine Farbauswahl zu öffnen, die den RGB\-Wert für Sie festgelegt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer>|Ermöglicht den Zugriff auf Objekte, auf die erhaltene Updateinformationen verwendet werden, die im **Eigenschaften** Fenster angezeigt werden.  <xref:Microsoft.VisualStudio.Shell.Interop.ISelectionContainer> wird von VSPackages für jedes Fenster implementiert, das auswählbare Objekte mit den zugehörigen Eigenschaften enthält, die angezeigt werden soll.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.ITypeInfo>|Stellt Informationen über den Typ eines Objekts als Methoden einer Schnittstelle und die Felder einer Struktur bereit.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection>|Aktiviert die Benachrichtigung von VSPackages Auswahl von Ereignissen zu empfangen und Informationen zur aktuellen Projekthierarchie, das Element, den Elementwert Befehlsbenutzeroberflächen und den Kontext abrufen.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsMultiItemSelect>|Stellt die Umgebung mit Zugriff auf die Mehrfachauswahl.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>|Wird verwendet, um lokalisierte Namen für einige Eigenschaften anzugeben **Eigenschaften** im Fenster angezeigt.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsSelectionEvents>|Notifies registrierte VSPackages von Änderungen an der aktuellen Auswahl oder dem Elementwert am Befehlsbenutzeroberflächen Elementkontext.|  
|<xref:Microsoft.VisualStudio.Shell.Interop.IVsTrackSelectionEx>|Benachrichtigt die Umgebung über eine Änderung in der aktuellen Auswahl und bietet Zugriff auf die Hierarchien\- und Elementinformationen in Bezug auf die neue Auswahl.|  
  
 Weitere Informationen zu `IDispatch`finden Sie in der MSDN Library.  
  
## Siehe auch  
 [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md)   
 [Eigenschaften\-Fenster Felder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md)