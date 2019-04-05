---
title: VSPackage-Status | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- state, VSPackages
- VSPackages, managing application state
- state persistence
ms.assetid: 6056a9ea-e7a8-481c-9fc8-340229fa12d9
caps.latest.revision: 25
manager: jillfra
ms.openlocfilehash: f3140b527673f87b1d7c552e99584232494aed7f
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961326"
---
# <a name="vspackage-state"></a>VSPackage-Status
Viele Faktoren ermitteln, welche persistenten Werte oder Zustand, der eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Anwendung.  
  
- Projekte verfügen über Projekt-und Konfiguration.  
  
- Lösungen verfügen über Eigenschaften.  
  
- Einstellungen des Benutzers bestimmen die Größe und Position von Dokumentfenstern, Toolfenster, Andockstatus und Tastenkombinationen in Visual Studio.  
  
- Anwendungen können Optionen haben die Benutzer festlegen.  
  
- Objekte, die eine Anwendung erstellt haben ihre eigenen Eigenschaften.  
  
  Hier sind einige der Möglichkeiten, eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Anwendungszustand verwaltet werden kann:  
  
- Über die Eigenschaftenseiten Projekt- und Projektmappendateien.  
  
- Über die **-Import / Export-Assistenten-Einstellungen**, wodurch einen Benutzer Einstellungen von einem Computer auf einen anderen zu verschieben.  
  
- Durch die **Optionen** Dialogfeld, das Optionen, die im Zusammenhang mit Anwendungen enthält.  
  
- Durch die **Eigenschaften** Fenster, in dem Eigenschaften von Objekten verfügbar macht.  
  
- Durch die Automatisierung. Eine Anwendung kann es sich um VSPackage und Objekteigenschaften zugreifen, die für die Benutzeroberflächenautomatisierung verfügbar gemacht wurden.  
  
  Zugrunde liegende Zustand der Anwendung sind verschiedene Persistenz-Mechanismen, mit die Zustand der Anwendung gespeichert und wiederhergestellt werden können.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unterstützung von Statuspersistenz](../misc/support-for-state-persistence.md)  
 Enthält allgemeine Strategien zum Speichern, Wiederherstellen und Zurücksetzen des Zustands eines VSPackage.  
  
 [Optionen und Optionsseiten](../extensibility/internals/options-and-options-pages.md)  
 Führt allgemeine und benutzerdefinierte Seiten für Optionen und erläutert, wie Sie diese Modelle installieren.  
  
 [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md)  
 Erstellen Sie zwei Optionen-Seiten, eine einfache Seite und einer benutzerdefinierten Seite erläutert.  
  
 [Unterstützung für Einstellungskategorien](../misc/support-for-settings-categories.md)  
 Erläutert, benutzereinstellungen und wie sie erstellt und persistent gespeichert werden.  
  
 [Erstellen einer Einstellungskategorie](../extensibility/creating-a-settings-category.md)  
 Erläutert das Erstellen einer [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Einstellungskategorie und zum Speichern von Werten, und Werte aus einer Datei wiederherstellen.  
  
 [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)  
 Erläutert das Anzeigen und ändern Sie den Wert eines Objekts in der **Eigenschaften** Fenster.  
  
 [Verfügbarmachen von Eigenschaften im Eigenschaftenfenster](../extensibility/exposing-properties-to-the-properties-window.md)  
 Erläutert, wie die öffentlichen Eigenschaften eines Objekts verfügbar zu machen die **Eigenschaften** Fenster.  
  
 [Unterstützung für Projekt- und Konfigurationseigenschaften](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Erläutert das Anzeigen und Ändern von Projekt-und Konfiguration.  
  
 [Abrufen von Projekteigenschaften](../extensibility/getting-project-properties.md)  
 Führt Sie durch die Schritte zum Erstellen eines verwalteten VSPackages, die Projekteigenschaften in einem Toolfenster anzeigt.  
  
 [Verwenden des Einstellungsspeichers](../extensibility/using-the-settings-store.md)  
 Erläutert, die Einstellungen für Store-persistenzmechanismus und seiner Verwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Stellt eine allgemeine Orientierung zu Themen, die erläutern, wie zum Erstellen und Verwenden von VSPackages bereit.