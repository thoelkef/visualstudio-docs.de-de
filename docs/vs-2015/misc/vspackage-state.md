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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62979994"
---
# <a name="vspackage-state"></a>VSPackage-Status
Viele Faktoren bestimmen den Satz von beibehaltenen Werten oder den Status einer- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Anwendung.  
  
- Projekte verfügen über Projekt-und Konfigurations Eigenschaften.  
  
- Projektmappen verfügen über Eigenschaften.  
  
- Benutzereinstellungen bestimmen die Größe und Position von Dokument Fenstern, Tool Fenstern, Andock Zustand und Tastenkombinationen.  
  
- Anwendungen können von einem Benutzer festgelegt werden.  
  
- Objekte, die von einer Anwendung erstellt werden, können eigene Eigenschaften haben.  
  
  Im folgenden finden Sie einige Möglichkeiten, wie ein [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Anwendungs Zustand verwaltet werden kann:  
  
- Über die Eigenschaften Seiten Projekt und Projekt Mappe.  
  
- Mithilfe des **Assistenten zum Importieren und Exportieren von Einstellungen**können Benutzereinstellungen von einem Computer auf einen anderen verschieben.  
  
- Über das Dialogfeld **Optionen** , das Optionen im Zusammenhang mit Anwendungen enthält.  
  
- Über das **Eigenschaften** Fenster, das Eigenschaften von Objekten verfügbar macht.  
  
- Durch Automatisierung. Eine Anwendung kann auf VSPackage und Objekteigenschaften zugreifen, die für die Automatisierung verfügbar gemacht wurden.  
  
  Zugrunde liegende Anwendungs Status sind verschiedene Dauerhaftigkeits Mechanismen, mit denen der Anwendungs Zustand gespeichert und wieder hergestellt werden kann.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Unterstützung von Statuspersistenz](../misc/support-for-state-persistence.md)  
 Enthält allgemeine Strategien zum Speichern, Wiederherstellen und Zurücksetzen des Zustands eines VSPackage.  
  
 [Optionen und Optionsseiten](../extensibility/internals/options-and-options-pages.md)  
 Führt allgemeine und benutzerdefinierte Options Seiten ein und erläutert, wie diese implementiert werden.  
  
 [Erstellen einer Optionsseite](../extensibility/creating-an-options-page.md)  
 Erläutert das Erstellen von zwei Options Seiten, einer einfachen Seite und einer benutzerdefinierten Seite.  
  
 [Unterstützung für Einstellungskategorien](../misc/support-for-settings-categories.md)  
 Erläutert Benutzereinstellungen und wie diese erstellt und persistent gespeichert werden.  
  
 [Erstellen einer Einstellungskategorie](../extensibility/creating-a-settings-category.md)  
 Erläutert, wie eine [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Einstellungs Kategorie erstellt und verwendet wird, um Werte in einer Einstellungsdatei zu speichern und Werte wiederherzustellen.  
  
 [Erweitern von Eigenschaften und des Eigenschaftenfensters](../extensibility/extending-properties-and-the-property-window.md)  
 Erläutert, wie der Wert eines Objekts im **Eigenschaften** Fenster angezeigt und geändert wird.  
  
 [Verfügbarmachen von Eigenschaften im Eigenschaftenfenster](../extensibility/exposing-properties-to-the-properties-window.md)  
 Erläutert, wie die öffentlichen Eigenschaften eines Objekts im **Eigenschaften** Fenster verfügbar gemacht werden.  
  
 [Unterstützung für Projekt- und Konfigurationseigenschaften](../extensibility/internals/support-for-project-and-configuration-properties.md)  
 Erläutert das Anzeigen und Ändern von Projekt-und Konfigurations Eigenschaften.  
  
 [Abrufen von Projekteigenschaften](../extensibility/getting-project-properties.md)  
 Führt Sie durch die Schritte zum Erstellen eines verwalteten VSPackages, das Projekteigenschaften in einem Tool Fenster anzeigt.  
  
 [Verwenden des Einstellungsspeichers](../extensibility/using-the-settings-store.md)  
 Erläutert den Beibehaltungs Mechanismus für den Einstellungs Speicher und seine Verwendung.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [VSPackages](../extensibility/internals/vspackages.md)  
 Bietet eine allgemeine Orientierung zu Themen, in denen das Erstellen und Verwenden von VSPackages erläutert wird.