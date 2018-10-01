---
title: Eigenschaftenseiten | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
caps.latest.revision: 13
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 544f69a8cfa90c7977a2861452fa47a570eb0bbb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47515348"
---
# <a name="property-pages"></a>Eigenschaftenseiten
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Eigenschaftenseiten](https://docs.microsoft.com/visualstudio/extensibility/internals/property-pages).  
  
Benutzer können anzeigen und Ändern von konfigurationsabhängig und -unabhängig Projekteigenschaften mit Eigenschaftenseiten. Ein **Eigenschaftenseiten** Schaltfläche ist aktiviert, der **Eigenschaften** Fenster oder auf der Symbolleiste des Projektmappen-Explorer für Objekte, die eine Eigenschaft Seitenansicht des ausgewählten Objekts bereitstellen. Eigenschaftenseiten werden von der Umgebung erstellt und stehen für Projektmappen und Projekten. Sie können jedoch auch sein, zur Verfügung gestellt, für Projektelemente, die Stellen konfigurationsabhängigen Eigenschaften verwenden. Diese Funktion kann verwendet werden, wenn Dateien in einem Projekt auf andere Compiler Switch-Einstellungen ordnungsgemäß erstellt erforderlich ist.  
  
## <a name="using-property-pages"></a>Verwenden von Eigenschaftenseiten  
 Wenn auf einer Eigenschaftenseite wird bereits angezeigt, und die Auswahl (z. B. aus einer Projektmappe ein Projekt), die Informationen in der Seiten ändern ändert, um die Eigenschaften für die neue Auswahl anzuzeigen. Wenn es keine Eigenschaften für das Objekt, die Eigenschaftenseiten zu unterstützen sind, ist die Eigenschaftenseite leer.  
  
 Wenn mehrere Objekte ausgewählt sind, zeigt die Eigenschaftenseite die Schnittmenge von Eigenschaften für alle ausgewählten Elemente. Wenn das ausgewählte Element keine konfigurationsabhängigen Eigenschaften und die **Eigenschaftenseiten** auf der Symbolleiste des Projektmappen-Explorer auf die Schaltfläche geklickt wird, der Fokus geändert wird, um das Fenster "Eigenschaften". Weitere Informationen über das Fenster "Eigenschaften" und die Auswahl, finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).  
  
 Wenn Eigenschaften für mehrere Objekte angezeigt werden, und Sie können einen Wert auf einer Eigenschaftenseite ändern, werden alle Werte für die Objekte in den neuen Wert festgelegt, selbst wenn zunächst verschiedene Kacheln, und die Seite leer war, wenn ein einzelnes Objekt Eigenschaften angezeigt wurden.  
  
 Es gibt zwei allgemeine Arten von **ProjectProperty Seiten** Dialogfelder in verfügbaren [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Im ersten, für die Visual Basic-Projekten werden z. B. die Eigenschaftenseiten angezeigt mit einem Feldformat, wie im folgenden Screenshot gezeigt. Im zweiten Fall weiter unten in diesem Abschnitt wird die Eigenschaft Seite Hosts ein Eigenschaftenraster ähnlich wie das im Fenster Eigenschaften.  
  
 ![Visual Basic-Eigenschaftenseiten](../../extensibility/internals/media/vsvbproppages.gif "VsVBPropPages")  
Projekt-Eigenschaftenseiten-Dialogfeld mit Feldstruktur Format und Struktur  
  
 Die Struktur im Dialogfeld "Eigenschaftenseiten" wird nicht mit erstellt <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>. Die Umgebung, auf der Grundlage von Namens des Ebenen, die an sie übergeben die <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> und die <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> -Schnittstellen, die sie erstellt.  
  
 Es stehen nur zwei Kategorien der obersten Ebene auf [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Eigenschaftenseiten:  
  
-   Allgemeine Eigenschaften, die der konfigurationsunabhängigen Informationen für das ausgewählte Objekt oder die Objekte angezeigt werden. Wenn einer der allgemeinen Eigenschaften für Unterkategorien ausgewählt ist, sind die Konfiguration, Plattform und Configuration Manager-Optionen am oberen Rand des Dialogfelds daher nicht verfügbar.  
  
-   Konfigurationseigenschaften, die konfigurationsabhängig Informationen zum Debuggen, Optimierung und Build-Parameter für die Projektmappe oder das Projekt enthält.  
  
 Weiteren Kategorien der obersten Ebene kann nicht erstellt werden, aber Sie können auch nicht eines dieser Zuordnungsverfahren angezeigt, in der Implementierung von `IVsPropertyPage`. Wenn Sie z. B. Sie keine konfigurationsunabhängigen Eigenschaften, die für ein Objekt angezeigt haben, können Sie auswählen, nicht die Kategorie der allgemeinen Eigenschaften anzuzeigen. Sie allgemeine Eigenschaften angezeigt, wenn `ISpecifyPropertyPages` wird aus Objekt für das Durchsuchen des Elements und Konfigurationseigenschaften implementiert, bei der Implementierung `ISpecifyPropertyPages` im Configuration-Objekt (die objektimplementierung `IVsCfg`, `IVsProjectCfg`, und die zugehörigen Schnittstellen).  
  
 Jede Kategorie, die unter einer Kategorie der obersten Ebene angezeigt wird und stellt eine separate Eigenschaft dar. Category und Subcategory verfügbaren Einträge im Dialogfeld werden durch die Implementierung von bestimmt `ISpecifyPropertyPages` und `IVsPropertyPage`.  
  
 `IDispatch` Objekte, die für Elemente im Auswahlcontainer mit Eigenschaften, die auf die Seiten implementieren Eigenschaft angezeigt werden `ISpecifyPropertyPages` eine Liste der Klassen-IDs aufgelistet werden. Die Klassen-IDs werden als Variablen übergeben `ISpecifyPropertyPages` und werden verwendet, um die Eigenschaftenseiten zu instanziieren. Die Liste der Klassen-IDs wird ebenfalls übergeben, um `IVsPropertyPage` um die Struktur auf der linken Seite des Dialogfelds zu erstellen. Die Eigenschaftenseiten und das Übergeben von Informationen zurück an die `IDispatch` Objekt, das implementiert `ISpecifyPropertyPages` und die Informationen für jede Seite.  
  
 Die Eigenschaften der durchsuchen-Objekts abgerufen werden, mithilfe von `IDispatch` für die einzelnen Objekte im Auswahlcontainer.  
  
 Implementieren von `Help::DisplayTopicFromF1Keyword` in Ihrem VSPackage bietet Sie die Funktionen für die Schaltfläche "Hilfe".  
  
 Weitere Informationen finden Sie unter `IDispatch` und `ISpecifyPropertyPages`in der MSDN Library.  
  
 Der zweite Typ der Eigenschaftenseiten angezeigt in den Beispielen Hosts eine Form der Eigenschaftsraster an, wie im folgenden Screenshot gezeigt.  
  
 ![VC aus Seiten](../../extensibility/internals/media/vsvcproppages.gif "VsVCPropPages")  
Dialogfeld mit dem Eigenschaftenraster Eigenschaftenseiten  
  
 Die Schnittstellen `IVSMDPropertyBrowser` und `IVSMDPropertyGrid` (deklariert in vsmanaged.h) dienen zum Erstellen und füllen Sie das Eigenschaftenraster in einem Dialogfeld oder Fenster.  
  
 Die Architektur von Projekten erheblich von früheren Versionen von geändert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]. Insbesondere ist das Konzept von welchem Projekt aktiv geändert hat. In [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], es gibt kein Konzept für ein aktives Projekt. In vorherigen entwicklungsumgebungen wurde das aktive Projekt an, dass das Projekt, das Erstellen und Bereitstellen von Befehlen unabhängig vom Kontext Standardmäßig verwendet wird. Jetzt die Lösung steuert und vermittelt, die beim Erstellen und Bereitstellen von Befehlen, welche Projekte angewendet.  
  
 Was zuvor ein aktives Projekt ist jetzt in einem der drei verschiedene Arten erfasst werden:  
  
-   Startprojekt  
  
     Sie können angeben, ein Projekt oder in Projekten, aus der Projektmappe-Eigenschaftenseite, die gestartet wird, wenn der Benutzer F5 drücken oder im Menü Build ausführen auswählt. Dies funktioniert ähnlich wie auf dem alten aktiven Projekt, in dem Sinne, dass der Name mit fett formatierter Schrift im Projektmappen-Explorer angezeigt wird.  
  
     Sie können das Startprojekt als Eigenschaft im Automatisierungsmodell abrufen, durch den Aufruf `DTE.Solution.SolutionBuild.StartupProjects`. In einem VSPackage, rufen Sie die <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> Methoden. `IVsSolutionBuildManager` steht als einen Dienst nach `QueryService` auf SID_SVsSolutionBuildManager. Weitere Informationen finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md) und [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   Aktive Projektmappenkonfiguration  
  
     [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] verfügt über eine aktive Projektmappenkonfiguration, verfügbar im Automatisierungsmodell durch die Implementierung `DTE.Solution.SolutionBuild.ActiveConfiguration`. Eine Projektmappenkonfiguration ist eine Sammlung mit einer Projektkonfiguration für jedes Projekt in der Projektmappe (jedes Projekt kann mehrere Konfigurationen für mehrere Plattformen mit unterschiedlichen Namen haben). Weitere Informationen im Zusammenhang mit der Projektmappe-Eigenschaftenseiten finden Sie unter [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).  
  
-   Aktuell ausgewählten Projekt  
  
     Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> Methode, um die Projekthierarchie und das Projektelement oder die ausgewählten Elemente abzurufen. Von DTE, verwenden Sie die `SelectedItems.SelectedItem.Project` und `SelectedItems.SelectedItem.ProjectItem` Methoden. Es ist Beispielcode unter die Spaltenüberschriften in die wichtigsten [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Dokumente.  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>   
 [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)   
 [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)   
 [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)

