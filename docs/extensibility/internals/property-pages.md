---
title: Eigenschaftenseiten | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 1b08e210a57388d77859600c02c0e6a30a404884
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="property-pages"></a>Eigenschaftenseiten
Benutzer können anzeigen und ändern die konfigurationsabhängigen "und"-unabhängigen Projekteigenschaften mit Eigenschaftenseiten. Ein **Eigenschaftenseiten** Schaltfläche ist aktiviert, der **Eigenschaften** Fenster oder auf der Symbolleiste des Projektmappen-Explorers für Objekte, die eine Eigenschaft Seitenansicht des ausgewählten Objekts bereitzustellen. Eigenschaftenseiten werden von der Umgebung erstellt und sind für Projektmappen und Projekten verfügbar. Sie können jedoch auch sein zur Verfügung gestellt, für Projektelemente, die stellen die konfigurationsabhängigen Eigenschaften verwenden. Diese Funktion kann verwendet werden, wenn Dateien in einem Projekt anderen Compiler Switch-Einstellungen korrekt erforderlich ist.  
  
## <a name="using-property-pages"></a>Verwenden von Eigenschaftenseiten  
 Wenn eine Eigenschaftenseite wird bereits angezeigt, und die Auswahl ändert (z. B. aus einer Projektmappe ein Projekt), die Informationen in der Seiten ändert sich zum Anzeigen der Eigenschaften für die neue Auswahl angezeigt. Wenn keine Eigenschaften für das Objekt, das für die Unterstützung von Eigenschaftenseiten vorhanden sind, ist die Eigenschaftsseite "leer.  
  
 Wenn mehrere Objekte ausgewählt sind, zeigt die Eigenschaftsseite "die Schnittmenge von Eigenschaften für alle ausgewählten Elemente. Wenn das ausgewählte Element keine konfigurationsabhängigen Eigenschaften enthält und die **Eigenschaftenseiten** auf der Symbolleiste des Projektmappen-Explorers auf die Schaltfläche geklickt wird, den Fokus auf das Eigenschaftenfenster ändert. Weitere Informationen im Zusammenhang mit dem Fenster "Eigenschaften" und der Auswahl finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
 Wenn Eigenschaften für mehrere Objekte angezeigt werden, und Sie einen Wert auf einer Eigenschaftenseite ändern, werden alle Werte für die Objekte in den neuen Wert festgelegt, selbst wenn zunächst andere Waren und die Seite war leer, wenn Eigenschaften des jeweiligen Objekts angezeigt wurden.  
  
 Es gibt zwei allgemeine Arten von **ProjectProperty Seiten** Dialogfelder in verfügbaren [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. In der ersten für Visual Basic-Projekten werden z. B. die Eigenschaftenseiten angezeigt mit einem Feldformat, wie im folgenden Screenshot gezeigt. Im zweiten Fall weiter unten in diesem Abschnitt wird die Eigenschaft Seite Hosts ein Eigenschaftenraster im Eigenschaftenfenster ähnelt.  
  
 ![Visual Basic-Eigenschaftenseiten](../../extensibility/internals/media/vsvbproppages.gif "VsVBPropPages")  
Projekt-Eigenschaftenseiten-Dialogfeld mit Feld Format und Struktur-Struktur  
  
 Die Struktur im Dialogfeld Eigenschaftenseiten nicht basiert auf <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Die Umgebung auf Grundlage der Ebenenname durch Übergeben der <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> und der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> kommuniziert, wird erstellt.  
  
 Es stehen nur zwei Kategorien der obersten Ebene auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Eigenschaftenseiten:  
  
-   Allgemeine Eigenschaften, die der Konfiguration unabhängig von Informationen für das ausgewählte Objekt oder die Objekte angezeigt werden. Wenn eine allgemeine Eigenschaften Unterkategorien aktiviert ist, sind die Konfiguration, Plattform und Configuration Manager-Optionen am oberen Rand des Dialogfelds daher nicht verfügbar.  
  
-   Konfigurationseigenschaften, die die konfigurationsabhängigen Informationen im Zusammenhang mit Debuggen, Optimierung und Build-Parameter für die Projektmappe oder das Projekt enthält.  
  
 Sie können zusätzlichen Kategorien der obersten Ebene können nicht erstellt, aber Sie können auswählen, nicht in der Implementierung eines dieser Zuordnungsverfahren anzuzeigen `IVsPropertyPage`. Wenn Sie z. B. Sie keine konfigurationsunabhängigen Eigenschaften, die für ein Objekt angezeigt haben, können Sie auswählen, nicht die Kategorie der allgemeinen Eigenschaften anzuzeigen. Sie allgemeine Eigenschaften angezeigt, wenn `ISpecifyPropertyPages` wird aus Objekt für das Element das Durchsuchen und Konfigurationseigenschaften implementiert, bei der Implementierung `ISpecifyPropertyPages` im Configuration-Objekt (das Objekt, durch `IVsCfg`, `IVsProjectCfg`, und die zugehörigen Schnittstellen).  
  
 Jede Kategorie angezeigt, die eine Kategorie der obersten Ebene stellt eine separate Eigenschaftenseite dar. Kategorie und Unterkategorie verfügbaren Einträge im Dialogfeld werden durch Ihre Implementierung von bestimmt `ISpecifyPropertyPages` und `IVsPropertyPage`.  
  
 `IDispatch` Objekte für Elemente im Auswahlcontainer mit Eigenschaften, die auf die Eigenschaft Seiten implementieren angezeigt werden `ISpecifyPropertyPages` eine Liste der Klassen-IDs auflisten. Die Klassen-IDs werden als Variablen übergeben `ISpecifyPropertyPages` und werden verwendet, um die Eigenschaftenseiten zu instanziieren. Die Liste der Klassen-IDs wird auch übergeben `IVsPropertyPage` zum Erstellen der Struktur auf der linken Seite des Dialogfelds. Übergeben von Informationen für die Eigenschaftenseiten anschließend zurück an den `IDispatch` Objekt, das implementiert `ISpecifyPropertyPages` und die Informationen für jede Seite eingetragen.  
  
 Mithilfe der Eigenschaften des Objekts durchsuchen abgerufen `IDispatch` für jedes Objekt in der Auswahlcontainer.  
  
 Implementieren von `Help::DisplayTopicFromF1Keyword` in Ihrem VSPackage stellt die Funktionalität für die Schaltfläche "Hilfe".  
  
 Weitere Informationen finden Sie unter `IDispatch` und `ISpecifyPropertyPages`in der MSDN Library.  
  
 Der zweite Typ der Eigenschaftenseiten angezeigt in den Beispielen Hosts eine Form des Rasters Eigenschaften an, wie im folgenden Screenshot gezeigt.  
  
 ![VC-aus-Seiten](../../extensibility/internals/media/vsvcproppages.gif "VsVCPropPages")  
Dialogfeld-Eigenschaftenseiten mit Eigenschaften (Raster)  
  
 Die Schnittstellen `IVSMDPropertyBrowser` und `IVSMDPropertyGrid` (deklariert in vsmanaged.h) dienen zum Erstellen und füllen Sie das Eigenschaftenraster in einem Dialogfeld oder Fenster.  
  
 Die Architektur von Projekten aus früheren Versionen von erheblich geändert hat [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Insbesondere ist das Konzept von dem Projektmanager aktiv geändert hat. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], ist es kein Konzept für ein aktives Projekt. In vorherigen entwicklungsumgebungen wurde das aktive Projekt an, dass das Projekt, das Erstellen und Bereitstellen von Befehlen unabhängig von den Kontext Standardmäßig würde. Nun die Projektmappe steuert und verhandelt wird das Erstellen und Bereitstellen von Befehlen gelten für die Projekte aus.  
  
 Was zuvor ein aktives Projekt ist jetzt in einem von drei verschiedenen Methoden erfasst:  
  
-   Das Startup-Projekt  
  
     Sie können angeben, ein Projekt oder in Projekten auf die Projektmappe-Eigenschaftenseite, die gestartet wird, wenn der Benutzer, drücken F5, oder führen Sie im Buildmenü wählt. Dies funktioniert ähnlich wie das alte aktive Projekt in dem Sinne, dass der Name im Projektmappen-Explorer mit fett angezeigt wird.  
  
     Sie können das Startup-Projekt als Eigenschaft in das Automatisierungsmodell abrufen, durch den Aufruf `DTE.Solution.SolutionBuild.StartupProjects`. In einem VSPackage, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> Methoden. `IVsSolutionBuildManager` steht als einen Dienst durch `QueryService` auf SID_SVsSolutionBuildManager. Weitere Informationen finden Sie unter [Projekt Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md) und [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   Aktive Projektmappenkonfiguration  
  
     [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verfügt über eine aktive Projektmappenkonfiguration, verfügbar im Automatisierungsmodell durch die Implementierung `DTE.Solution.SolutionBuild.ActiveConfiguration`. Eine Projektmappenkonfiguration ist eine Auflistung mit einer Projektkonfiguration für jedes Projekt in der Projektmappe (jedes Projekt kann mehrere Konfigurationen auf mehreren Plattformen, sodass unterschiedliche Namen haben). Weitere Informationen im Zusammenhang mit dem Projektmappen-Eigenschaftenseiten finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   Aktuell ausgewählte Projekt  
  
     Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> Methode zum Abrufen der Projekthierarchie und Projektelement oder Elemente ausgewählt. Von DTE, verwenden Sie die `SelectedItems.SelectedItem.Project` und `SelectedItems.SelectedItem.ProjectItem` Methoden. Ist es Beispielcode unter dieser Überschriften im Kern [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Dokumente.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Projekt-Konfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)