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
ms.openlocfilehash: b5d2e7d15f7b479941c3186d8cd694c92f762bbf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690998"
---
# <a name="extending-properties"></a>Erweitern von Eigenschaften
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Das [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **Eigenschaften** Fenster ist ein universeller Eigenschaften Browser für com-und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Produkte. Das **Eigenschaften** Fenster funktioniert mit `ITypeInfo` Typinformationen und com+-Metadaten, um die Entwurfszeit Eigenschaften für das aktuell ausgewählte Objekt in einem beliebigen anderen Fenster in der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) aufzulisten.  
  
 Das **Eigenschaften** Fenster, das durch Drücken von F4 auf der Tastatur oder durch Auswahl von **Eigenschaften Fenster** im Menü **Ansicht** geöffnet werden kann, wird zum Anzeigen und Bearbeiten von Konfigurations unabhängigen Entwurfszeit Eigenschaften und-Ereignissen ausgewählter Objekte verwendet. Konfigurations abhängige Eigenschaften, die Projektmappen und Projekten zugeordnet sind, werden auf den Eigenschaften [Seiten](../../extensibility/internals/property-pages.md)angezeigt. Weitere Informationen finden Sie unter [NIB: Projekteigenschaften](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50), [Verwalten von Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md)und [NIB: Element Verwaltung in Projekten](https://msdn.microsoft.com/762e606b-7f44-4b66-97a1-e30a703654a0).  
  
 ![Übersicht über Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "vspropertieswindow")  
Eigenschaftenfenster  
  
 Dieser Abschnitt enthält ausführliche Informationen zu den einzelnen Bereichen des Fensters **Eigenschaften** und zu den Schnittstellen, die Sie implementieren müssen, und zum Auffüllen des Fensters aufzurufen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)  
 Erläutert den Zweck des **Eigenschaften** Fensters in Relation zum Tool Fenster und Dokument Fenster.  
  
 [Vorlagenrichtlinie und das Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen Projekt enthalten ist und wie dieses Enterprise-Vorlagen Projekt Richtlinien erzwingen kann.  
  
 [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen im **Eigenschaften** Fenster angezeigt werden.  
  
 [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md)  
 Beschreibt den Zweck der Objektliste **Eigenschaften** Fenster, in dem beschrieben wird, dass die Umgebung, wenn ein anderes Objekt aus dieser Liste einen-Befehl auslöst, informiert wird, dass ein neues-Objekt ausgewählt wurde.  
  
 [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md)  
 Erläutert den Zweck der vier Standard Schaltflächen, die auf der Symbolleiste des **Eigenschaften** Fensters angezeigt werden.  
  
 [Anzeigeraster für Eigenschaften](../../extensibility/internals/properties-display-grid.md)  
 Erläutert, wo sich die Felder Eigenschaften Namen und Eigenschaftswerte im Raster befinden.  
  
 [Ankündigen der Auswahlnachverfolgung im Eigenschaftenfenster](../../misc/announcing-property-window-selection-tracking.md)  
 Beschreibt die Auswahl Nachverfolgung für das **Eigenschaften** Fenster.  
  
 [Ausblenden von Eigenschaftenfenster mit untergeordneten Eigenschaften](../../misc/hiding-properties-that-have-child-properties.md)  
 Erläutert, wie Eigenschaften mit untergeordneten Eigenschaften durch Implementieren der- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> Schnittstelle ausgeblendet werden.  
  
 [Bereitstellen eines benutzerdefinierten Eigenschaftenfensters](../../misc/providing-a-custom-properties-window.md)  
 Beschreibt die Schritte zum Bereitstellen eines eigenen Eigenschaften Browsers.  
  
 [Abrufen von Feldbeschreibungen im Eigenschaftenfenster](../../misc/getting-field-descriptions-from-the-properties-window.md)  
 Erläutert, wo der Beschreibungs Bereich zu finden ist, der Informationen im Zusammenhang mit dem ausgewählten Eigenschaften Feld anzeigt.  
  
 [Aktualisieren von Eigenschaftswerten im Eigenschaftenfenster](../../misc/updating-property-values-in-the-properties-window.md)  
 Enthält Schritt-für-Schritt-Anweisungen, die die zwei Möglichkeiten zum Synchronisieren des **Eigenschaften** Fensters mit Eigenschafts Wertänderungen anzeigen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Erläutert Projekte als Bausteine der [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE.  
  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Plattform zum fortlaufenden testen und Debuggen von Anwendungen verwenden können, während Sie Sie erstellen.  
  
 [HTML-Dokumenteigenschaften, Eigenschaftenfenster](https://msdn.microsoft.com/library/46e3d164-a1a7-42f9-87b0-344e10a37b62)  
 Stellt Anweisungen zum Bearbeiten eines HTML-Dokuments direkt aus dem Eigenschaftenfenster bereit und stellt eine Tabelle bereit, in der die Felder in einem HTML-Dokument in der Eigenschaftenfenster beschrieben werden.  
  
 [IDispatch](https://msdn.microsoft.com/ebbff4bc-36b2-4861-9efa-ffa45e013eb5)  
 Beschreibt die- `IDispatch` Schnittstelle, die zuerst zur Unterstützung von Automation entwickelt wurde und einen spät gebundenen Mechanismus zum Zugreifen auf und Abrufen von Informationen über die Methoden und Eigenschaften eines Objekts bereitstellt.  
  
 [NIB: Einführung in dynamische Eigenschaften (Visual Studio)](https://msdn.microsoft.com/f5102027-1431-4195-ae40-9b991de46d3a)  
 Bietet einen Überblick über dynamische Eigenschaften, mit denen Sie Ihre Anwendung so konfigurieren können, dass Eigenschaftswerte in einer externen Konfigurationsdatei anstatt im kompilierten Code der Anwendung gespeichert werden.  
  
 [NIB:Projekte als Container](https://msdn.microsoft.com/87d40f63-f487-4767-8963-64beec27ba1b)  
 Beschreibt die Rolle des Projekts als Container in einer Projekt Mappe, um die Elemente, aus denen Ihre Anwendung besteht, logisch zu verwalten, zu erstellen und zu debuggen.  
  
 [NIB: Projekteigenschaften](https://msdn.microsoft.com/fb126574-24ad-4c96-9b2b-6e1f3879ba50)  
 Beschreibt, wie das Projekteinstellungen verwaltet, mit denen Sie Eigenschaften steuern können, die für das gesamte Projekt gelten, sowie Eigenschaften, die auf bestimmte Buildkonfigurationen des Projekts beschränkt sind.  
  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)  
 Erläutert [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] die effiziente Verwaltung der Elemente, wie z. b. Verweise, Datenverbindungen, Ordner und Dateien, die für den Entwicklungsaufwand durch Projektmappen und Projekte erforderlich sind.  
  
 [Erweitern anderer Teile von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]-Komponenten passen.
