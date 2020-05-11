---
title: Eigenschaftenseiten | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration options, changing properties
- property pages
- property pages, changing configuration options
ms.assetid: b9b3e6e8-1e30-4c89-9862-330265dcf38c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac788f51bcdc52cd39469a272909890333c5016b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706054"
---
# <a name="property-pages"></a>Eigenschaftenseiten
Benutzer können projektkonfigurationsabhängige und -unabhängige Eigenschaften mithilfe von Eigenschaftenseiten anzeigen und ändern. Eine Schaltfläche **Eigenschaftenseiten** ist im **Eigenschaftenfenster** oder auf der Symbolleiste des Projektmappen-Explorers für Objekte aktiviert, die eine Eigenschaftenseitenansicht des ausgewählten Objekts bereitstellen. Eigenschaftenseiten werden von der Umgebung erstellt und sind für Lösungen und Projekte verfügbar. Sie können jedoch auch für Projektelemente verfügbar gemacht werden, die konfigurationsabhängige Eigenschaften verwenden. Diese Funktion kann verwendet werden, wenn Dateien in einem Projekt andere Compiler-Switch-Einstellungen benötigen, um ordnungsgemäß zu erstellen.

## <a name="using-property-pages"></a>Verwenden von Eigenschaftenseiten
 Wenn bereits eine Eigenschaftenseite angezeigt wird und sich die Auswahl ändert (z. B. von einer Projektmappe zu einem Projekt), ändern sich die auf den Seiten angezeigten Informationen, um die Eigenschaften für die neue Auswahl anzuzeigen. Wenn für das Objekt keine Eigenschaften vorhanden sind, die Eigenschaftenseiten unterstützen, ist die Eigenschaftenseite leer.

 Wenn mehrere Objekte ausgewählt sind, zeigt die Eigenschaftenseite den Schnittpunkt der Eigenschaften für alle ausgewählten Elemente an. Wenn das ausgewählte Element keine konfigurationsabhängigen Eigenschaften enthält und auf die Schaltfläche **Eigenschaftenseiten** auf der Symbolleiste des Projektmappen-Explorers geklickt wird, ändern Sie den Fokus auf das Eigenschaftenfenster. Weitere Informationen zum Fenster Eigenschaften und zur Auswahl finden Sie unter [Erweitern von Eigenschaften](../../extensibility/internals/extending-properties.md).

 Wenn Eigenschaften für mehrere Objekte angezeigt werden und Sie einen Wert auf einer Eigenschaftenseite ändern, werden alle Werte für die Objekte auf den neuen Wert festgelegt, auch wenn sie anfangs anders waren und die Seite leer war, als die Eigenschaften eines einzelnen Objekts angezeigt wurden.

 Es gibt zwei allgemeine Typen von **ProjectProperty** Pages-Dialogfeldern, die in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügbar sind. Im ersten, z. B. bei Visual Basic-Projekten werden die Eigenschaftenseiten in einem Feldformat angezeigt, wie im folgenden Screenshot gezeigt. Im zweiten Abschnitt, der weiter unten in diesem Abschnitt gezeigt wird, hostet die Eigenschaftenseite ein Eigenschaftenraster, das dem im Eigenschaftenfenster ähnelt.

 ![Visual Basic-Eigenschaftenseiten](../../extensibility/internals/media/vsvbproppages.gif "vsVBPropPages") Dialogfeld Projekteigenschaftsseiten mit Feldformat und Baumstruktur

 Die Struktur strukturim Dialogfeld Eigenschaftenseiten <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>wird nicht mit erstellt. Die Umgebung, basierend auf dem Ebenennamen, der von der <xref:Microsoft.VisualStudio.OLE.Interop.ISpecifyPropertyPages> und den <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage> Schnittstellen an sie übergeben wird, erstellt sie.

 Auf [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Eigenschaftenseiten sind nur zwei Kategorien der obersten Ebene verfügbar:

- Allgemeine Eigenschaften, die konfigurationsunabhängige Informationen für das ausgewählte Objekt oder die ausgewählten Objekte anzeigt. Wenn daher eine der Unterkategorien "Allgemeine Eigenschaften" ausgewählt ist, sind die Optionen Konfiguration, Plattform und Configuration Manager oben im Dialogfeld nicht verfügbar.

- Konfigurationseigenschaften, die konfigurationsabhängige Informationen zu Debugging-, Optimierungs- und Buildparametern für die Projektmappe oder das Projekt enthalten.

  Sie können keine zusätzlichen Kategorien der obersten Ebene erstellen, aber Sie können `IVsPropertyPage`in der Implementierung von die eine oder andere Nichtanzeige festlegen. Wenn Sie z. B. keine konfigurationsunabhängigen Eigenschaften für ein Objekt anzeigen können, können Sie die Kategorie "Allgemeine Eigenschaften" nicht anzeigen. Sie zeigen allgemeine `ISpecifyPropertyPages` Eigenschaften an, wenn sie aus dem Suchobjekt des Elements und den Konfigurationseigenschaften implementiert werden, wenn Sie im Konfigurationsobjekt implementieren `ISpecifyPropertyPages` (das Objekt, das , `IVsCfg` `IVsProjectCfg`und verwandte Schnittstellen implementiert).

  Jede Kategorie, die unter einer Kategorie der obersten Ebene angezeigt wird, stellt eine separate Eigenschaftenseite dar. Kategorie- und Unterkategorieeinträge, die im Dialogfeld `ISpecifyPropertyPages` `IVsPropertyPage`verfügbar sind, werden durch die Implementierung von und bestimmt.

  `IDispatch`Objekte für Elemente im Auswahlcontainer, deren Eigenschaften `ISpecifyPropertyPages` auf Eigenschaftenseiten angezeigt werden sollen, implementieren, um eine Liste von Klassen-IDs aufzulisten. Die Klassen-IDs werden `ISpecifyPropertyPages` als Variablen an übergeben und zum Instanziieren der Eigenschaftenseiten verwendet. Die Liste der Klassen-IDs `IVsPropertyPage` wird auch übergeben, um die Baumstruktur auf der linken Seite des Dialogfelds zu erstellen. Die Eigenschaftenseiten geben dann `IDispatch` Informationen an `ISpecifyPropertyPages` das Objekt zurück, das die Informationen für jede Seite implementiert und ausfüllt.

  Die Eigenschaften des Suchobjekts `IDispatch` werden mithilfe jedes Objekts im Auswahlcontainer abgerufen.

  Die `Help::DisplayTopicFromF1Keyword` Implementierung in Ihrem VSPackage bietet die Funktionalität für die Hilfeschaltfläche.

  Weitere Informationen finden `IDispatch` `ISpecifyPropertyPages`Sie in der MSDN-Bibliothek.

  Der zweite Typ von Eigenschaftenseiten, die in den Beispielen angezeigt werden, hostet eine Form des Eigenschaftenrasters, wie im folgenden Screenshot gezeigt.

  ![VC-Eigenschaftenseiten](../../extensibility/internals/media/vsvcproppages.gif "vsVCPropPages") Dialogfeld Eigenschaftenseiten mit Eigenschaftenraster

  Die Schnittstellen `IVSMDPropertyBrowser` `IVSMDPropertyGrid` und (deklariert in vsmanaged.h) werden verwendet, um das Eigenschaftenraster in einem Dialogfeld oder Fenster zu erstellen und aufzufüllen.

  Die Architektur von Projekten hat sich [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gegenüber früheren Versionen von erheblich verändert. Insbesondere hat sich der Begriff, welches Projekt aktiv ist, geändert. In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]gibt es kein Konzept für ein aktives Projekt. In früheren Entwicklungsumgebungen war das aktive Projekt das Projekt, auf das das Erstellen und Bereitstellen von Befehlen unabhängig vom Kontext standardmäßig eingestellt wurde. Nun wird die Lösung gesteuert und vermittelt, welche Build- und Bereitstellungsbefehle für welche Projekte gelten.

  Was früher ein aktives Projekt war, wird nun auf eine von drei verschiedenen Arten erfasst:

- Das Startup-Projekt

   Sie können ein Projekt oder Projekte auf der Eigenschaftenseite der Projektmappe angeben, die gestartet wird, wenn der Benutzer F5 drückt oder im Menü Build ausführen auswählt. Dies funktioniert ähnlich wie das alte aktive Projekt in dem Sinne, dass sein Name im Projektmappen-Explorer mit fett formatierter Schrift angezeigt wird.

   Sie können das Startprojekt als Eigenschaft im `DTE.Solution.SolutionBuild.StartupProjects`Automatisierungsmodell abrufen, indem Sie aufrufen. In einem VSPackage rufen <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> Sie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionBuildManager2.get_StartupProject%2A> die oder die Methoden auf. `IVsSolutionBuildManager`ist als Service `QueryService` auf SID_SVsSolutionBuildManager verfügbar. Weitere Informationen finden Sie unter [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md) und [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md).

- Aktive Lösungsbuildkonfiguration

   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]verfügt über eine aktive Lösungskonfiguration, `DTE.Solution.SolutionBuild.ActiveConfiguration`die im Automatisierungsmodell durch Implementierung von verfügbar ist. Eine Projektmappenkonfiguration ist eine Sammlung, die eine Projektkonfiguration für jedes Projekt in der Projektmappe enthält (jedes Projekt kann mehrere Konfigurationen auf mehreren Plattformen mit unterschiedlichen Namen aufweisen). Weitere Informationen zu den Eigenschaftenseiten der Lösung finden Sie unter [Lösungskonfiguration](../../extensibility/internals/solution-configuration.md).

- Derzeit ausgewähltes Projekt

   Implementieren <xref:Microsoft.VisualStudio.Shell.Interop.IVsMonitorSelection.GetCurrentSelection%2A> Sie die Methode zum Abrufen der Projekthierarchie und des oder der ausgewählten Projektelemente. Von DTE verwenden Sie `SelectedItems.SelectedItem.Project` `SelectedItems.SelectedItem.ProjectItem` die und Methoden. In den Kerndokumenten [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] befindet sich Beispielcode unter diesen Überschriften.

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPropertyPage>
- [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)
- [Projektkonfigurationsobjekt](../../extensibility/internals/project-configuration-object.md)
- [Projektmappenkonfiguration](../../extensibility/internals/solution-configuration.md)
