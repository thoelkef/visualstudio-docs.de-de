---
title: Erweitern von Eigenschaften | Microsoft-Dokumentation
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: fec1140bc90d494a0c611ed84786f364f17f6087
ms.lasthandoff: 02/22/2017

---
# <a name="extending-properties"></a>Erweitern von Eigenschaften
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster einen universellen Eigenschaftenbrowser für COM- und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Produkte. Die **Eigenschaften** Fenster arbeitet mit `ITypeInfo` Geben Sie Informationen und COM+-Metadaten, die zur Entwurfszeit Eigenschaften für das aktuell ausgewählte Objekt in einem anderen Fenster in der integrated Development Environment (IDE) aufgeführt.  
  
 Die **Eigenschaften** Fenster, die geöffnet werden kann, durch Drücken von F4 auf der Tastatur oder auswählen **Eigenschaftenfenster** auf der **Ansicht** Menü dient zum Anzeigen und Bearbeiten der Konfiguration unabhängig, Entwurfszeit-Eigenschaften und-Ereignisse ausgewählter Objekte. Die konfigurationsabhängigen Eigenschaften für Projektmappen und Projekte, werden angezeigt, auf [Eigenschaftenseiten](../../extensibility/internals/property-pages.md). Weitere Informationen finden Sie unter [NIB: Projekteigenschaften](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md), und [NIB: Item Management in Projects](http://msdn.microsoft.com/en-us/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Übersicht über Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow")  
Eigenschaftenfenster  
  
 Dieser Abschnitt enthält ausführliche Informationen zu den einzelnen Bereichen der der **Eigenschaften** Fenster und Schnittstellen, die Sie implementieren müssen, und rufen zum Auffüllen des Fensters.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)  
 Erläutert den Zweck der **Eigenschaften** Fensters in Bezug auf das Toolfenster und Dokumentfenster.  
  
 [Die Richtlinie für Vorlagen und im Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, und wie diese Enterprise-Vorlagenprojekt durchsetzen kann.  
  
 [Eigenschaften-Fenster Felder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster.  
  
 [Liste der Eigenschaften im Fenster Objekt](../../extensibility/internals/properties-window-object-list.md)  
 Beschreibt den Zweck der **Eigenschaften** Fensterliste beschreiben, wenn ein anderes Objekt aus dieser Liste einen Aufruf auslöst, die Umgebung informiert wird, dass ein neues Objekt ausgewählt wurde.  
  
 [Eigenschaften-Fenster-Schaltflächen](../../extensibility/internals/properties-window-buttons.md)  
 Erläutert den Zweck der vier Schaltflächen auf der **Eigenschaften** Symbolleiste des Fensters.  
  
 [Raster von Eigenschaften anzeigen](../../extensibility/internals/properties-display-grid.md)  
 Erläutert, wo die Eigenschaftennamen und Werte der Eigenschaftenfelder im Raster befinden.  
  
 [Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster](../../misc/announcing-property-window-selection-tracking.md)  
 Beschreibt die Auswahl für die **Eigenschaften** Fenster.  
  
 [Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften](../../misc/hiding-properties-that-have-child-properties.md)  
 Erklärt, wie Eigenschaften ausblenden, deren untergeordnete Eigenschaften durch Implementieren der <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>Schnittstelle.</xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>  
  
 [Bereitstellen eines benutzerdefinierten Eigenschaftenfensters](../../misc/providing-a-custom-properties-window.md)  
 Erläutert die Schritte zum Bereitstellen Ihrer eigenen Eigenschaftenbrowser.  
  
 [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Erläutert, wo Sie den Beschreibungsbereich finden, der Informationen im Zusammenhang mit dem ausgewählten Eigenschaftenfeld anzeigt.  
  
 [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](../../misc/updating-property-values-in-the-properties-window.md)  
 Bietet eine schrittweise Anleitung, die zeigen, die zwei Möglichkeiten, behalten die **Eigenschaften** Fenster synchronisiert mit Eigenschaftswert ändert.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Stellt das Projekten als Bausteine von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Plattform für kontinuierlich zu testen und zu debuggen, während Sie sie erstellen.  
  
 [HTML-Dokumenteigenschaften, Eigenschaftenfenster](http://msdn.microsoft.com/Library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Enthält Anweisungen zum Bearbeiten eines HTML-Dokuments im Eigenschaftenfenster aus, und enthält eine Tabelle, in die Felder in einem HTML-Dokument im Fenster Eigenschaften.  
  
 [IDispatch](http://msdn.microsoft.com/en-us/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Beschreibt die `IDispatch` -Schnittstelle, die zuerst, zur Unterstützung der Automatisierung entwickelt wurde, Bereitstellen eines spät gebundenen Mechanismus zum Zugreifen auf und das Abrufen von Informationen zu den Methoden und Eigenschaften eines Objekts.  
  
 [NIB: Einführung in dynamische Eigenschaften (Visual Studio)](http://msdn.microsoft.com/en-us/f5102027-1431-4195-ae40-9b991de46d3a)  
 Bietet einen Überblick über die dynamischen Eigenschaften, mit denen Sie Ihre Anwendung so konfigurieren, dass Werte in einer externen Konfigurationsdatei anstelle von kompilierten Code der Anwendung gespeichert sind.  
  
 [NIB: Projekte als Container](http://msdn.microsoft.com/en-us/87d40f63-f487-4767-8963-64beec27ba1b)  
 Beschreibt die Rolle des Projekts als Container für eine Lösung, die logisch zu verwalten, erstellen und Debuggen die Elemente, die die Anwendung bilden.  
  
 [NIB: Projekteigenschaften](http://msdn.microsoft.com/en-us/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Beschreibt, wie das Projekt Einstellungen verwaltet, mit denen Sie die Eigenschaften, die für das gesamte Projekt gelten, sowie Eigenschaften, die auf bestimmte Erstellungskonfigurationen des Projekts beschränkt sind.  
  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effizient verwaltet die Elemente wie z. B. Verweise, datenverbindungen, Ordner und Dateien, die von der Entwicklung über Projektmappen und Projekte erforderlich sind.  
  
 [Erweitern von anderen Teilen von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Services Benutzeroberflächenelemente zu erstellen, die den restlichen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].
