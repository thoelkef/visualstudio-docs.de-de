---
title: Erweitern von Eigenschaften | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 59afc6a95e327460602ece8db58f075b483d0e09
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62538289"
---
# <a name="extending-properties"></a>Erweitern von Eigenschaften
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Eigenschaften** Fenster ist eine universelle Eigenschaftenbrowser für COM- und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Produkte. Die **Eigenschaften** Fenster arbeitet mit `ITypeInfo` geben Informationen und COM+-Metadaten zum Auflisten der Eigenschaften zur Entwurfszeit für das aktuell ausgewählte Objekt in einem anderen Fenster in der integrierten Entwicklungsumgebung (IDE).  
  
 Die **Eigenschaften** Fenster, die geöffnet werden kann, indem Sie auf der Tastatur die Taste F4 drücken, oder wählen **Fenster "Eigenschaften"** auf die **Ansicht** Menübefehl, dient zum Anzeigen und bearbeiten während der Entwurfszeit konfigurationsunabhängigen Eigenschaften und Ereignissen ausgewählter Objekte. Konfigurationsabhängigen Eigenschaften für Projektmappen und Projekten, werden angezeigt, auf [Eigenschaftenseiten](../../extensibility/internals/property-pages.md). Weitere Informationen finden Sie unter [NIB: Projekteigenschaften](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md), und [NIB: Elementverwaltung in Projekten](http://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Übersicht über das Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "VsPropertiesWindow")  
Eigenschaftenfenster  
  
 Dieser Abschnitt enthält ausführliche Informationen zu den einzelnen Bereichen im Zusammenhang der **Eigenschaften** Fenster und die Schnittstellen, die Sie implementieren müssen, und Aufruf an das Fenster zu füllen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)  
 Erläutert den Zweck der **Eigenschaften** Fensters in Bezug auf das Toolfenster und Dokumentfenster.  
  
 [Vorlagenrichtlinie und das Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, und wie diese Enterprise-Vorlagenprojekt Richtlinie erzwingen kann.  
  
 [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster.  
  
 [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md)  
 Beschreibt den Zweck der der **Eigenschaften** Objektliste des Eigenschaftenfensters, beschreiben Sie, wenn ein anderes Objekt aus dieser Liste einen Aufruf ausgelöst wird, die Umgebung informiert wird, dass ein neues Objekt ausgewählt wurde.  
  
 [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md)  
 Erläutert den Zweck der vier Schaltflächen angezeigt werden, auf die **Eigenschaften** Symbolleiste des Fensters.  
  
 [Anzeigeraster für Eigenschaften](../../extensibility/internals/properties-display-grid.md)  
 Erläutert, in dem die Eigenschaftsnamen und Werte der Eigenschaftenfelder im Raster gefunden werden.  
  
 [Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster](../../misc/announcing-property-window-selection-tracking.md)  
 Beschreibt die Auswahl für die **Eigenschaften** Fenster.  
  
 [Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften](../../misc/hiding-properties-that-have-child-properties.md)  
 Erläutert, wie Eigenschaften ausblenden, die untergeordneten Eigenschaften durch die Implementierung der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Schnittstelle.  
  
 [Bereitstellen eines benutzerdefinierten Eigenschaftenfensters](../../misc/providing-a-custom-properties-window.md)  
 Werden die Schritte zum Bereitstellen von Ihren eigenen Eigenschaften-Browser.  
  
 [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Erläutert, wo Sie im Bereich für das finden, das Informationen im Zusammenhang mit dem ausgewählten Eigenschaftenfeld gehören anzeigt.  
  
 [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](../../misc/updating-property-values-in-the-properties-window.md)  
 Enthält schrittweise Anleitungen, die zeigen, zwei Möglichkeiten, behalten Sie die **Eigenschaften** Fenster mit Änderungen von Eigenschaftswerten synchronisiert.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Projekte wird erläutert, wie die Bausteine von der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Plattform für die fortlaufend testen und Debuggen von Anwendungen erstellen.  
  
 [HTML-Dokumenteigenschaften, Eigenschaftenfenster](http://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Enthält Anweisungen zum Bearbeiten von HTML-Dokument direkt aus dem Fenster "Eigenschaften", und stellt eine Tabelle, in die Felder in einem HTML-Dokument in das Fenster "Eigenschaften".  
  
 [IDispatch](http://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Beschreibt die `IDispatch` -Schnittstelle, die zuerst entwickelt wurde, um Automation, einen spät gebundenen Mechanismus zum zugreifen und Abrufen von Informationen zu den Methoden und Eigenschaften eines Objekts zu unterstützen.  
  
 [NIB: Einführung in dynamische Eigenschaften (Visual Studio)](http://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Bietet einen Überblick über die dynamischen Eigenschaften, mit denen Sie Ihre Anwendung so konfigurieren, dass Eigenschaftswerte in einer externen Konfigurationsdatei anstelle von kompilierten Code der Anwendung gespeichert sind.  
  
 [NIB: Projekte als Container](http://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Beschreibt die Rolle des Projekts als Container für eine Lösung für logisch zu verwalten, erstellen und Debuggen die Elemente, die die Anwendung bilden.  
  
 [NIB: Projekteigenschaften](http://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Beschreibt, wie das Projekt Einstellungen verwaltet, mit denen Sie die Eigenschaften des Steuerelements, die für das gesamte Projekt gelten, sowie Eigenschaften, die auf bestimmte Erstellungskonfigurationen des Projekts beschränkt sind.  
  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] effizient verwaltet die Elemente wie z. B. Verweise, datenverbindungen, Ordner und Dateien, die von der Entwicklung über Projektmappen und Projekte erforderlich sind.  
  
 [Erweitern anderer Teile von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Komponenten passen.
