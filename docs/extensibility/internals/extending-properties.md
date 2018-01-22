---
title: Erweitern von Eigenschaften | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
caps.latest.revision: "18"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 26cf161259736dbd2b2e26279842571d62f69352
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/22/2018
---
# <a name="extending-properties"></a>Erweitern von Eigenschaften
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster ist eine universelle Eigenschaftenbrowser für COM- und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Produkte. Die **Eigenschaften** Fenster arbeitet mit `ITypeInfo` geben Informationen und COM+-Metadaten zur Auflistung der Eigenschaften zur Entwurfszeit für das aktuell ausgewählte Objekt in einem anderen Fenster in der integrierten Entwicklungsumgebung (IDE).  
  
 Die **Eigenschaften** Fenster, die geöffnet werden kann, indem Sie auf der Tastatur die Taste F4 drücken oder auswählen **Fenster "Eigenschaften"** auf die **Ansicht** Menübefehl, dient zum Anzeigen und bearbeiten Konfiguration unabhängig, während der Entwurfszeit-Eigenschaften und-Ereignisse ausgewählter Objekte. Die konfigurationsabhängigen Eigenschaften, mit Projektmappen und Projekten, werden angezeigt, auf [Eigenschaftenseiten](../../extensibility/internals/property-pages.md). Weitere Informationen [Konfigurationsoptionen verwalten](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Übersicht über Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "VsPropertiesWindow")  
Eigenschaftenfenster  
  
 Dieser Abschnitt enthält ausführliche Informationen, die für die einzelnen Bereiche der bezieht sich die **Eigenschaften** Fenster und die Schnittstellen, die Sie implementieren müssen, und rufen zum Auffüllen des Fensters.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)  
 Erläutert den Zweck der **Eigenschaften** Fensters in Bezug auf das Toolfenster und Dokumentfenster angezeigt.  
  
 [Vorlagenrichtlinie und das Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, und wie diese Enterprise-Vorlagenprojekt Richtlinie erzwingen kann.  
  
 [Felder und Schnittstellen des Eigenschaftenfensters](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster.  
  
 [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md)  
 Beschreibt den Zweck der **Eigenschaften** Fenster Objektliste, beschreiben, wie bei ein anderen Objekt aus dieser Liste einen Aufruf wird ausgelöst, die Umgebung darüber informiert wird, dass ein neues Objekt ausgewählt wurde.  
  
 [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md)  
 Erläutert den Zweck der vier Schaltflächen auf der **Eigenschaften** Symbolleiste des Fensters.  
  
 [Anzeigeraster für Eigenschaften](../../extensibility/internals/properties-display-grid.md)  
 Erläutert, in dem die Eigenschaftsnamen und Werte der Eigenschaftenfelder im Raster gefunden werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Projekte als Bausteine von erläutert die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Plattform für die fortlaufend testen und Debuggen von Anwendungen erstellen.  
  
 [IDispatch](https://msdn.microsoft.com/library/windows/desktop/ms221608.aspx)  
 Beschreibt die `IDispatch` -Schnittstelle, die zuerst entwickelt wurde, um Automatisierung Bereitstellen eines spät gebundenen Mechanismus zum Zugreifen auf und Abrufen von Informationen zu den Methoden und Eigenschaften eines Objekts zu unterstützen.  
  
 [Verwalten von Anwendungseinstellungen (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Bietet eine Übersicht über Anwendungseinstellungen, mit denen Sie Ihre Anwendung so konfigurieren, dass Eigenschaftswerte in einer externen Konfigurationsdatei anstelle von kompilierten Code der Anwendung gespeichert sind.  
  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effizient verwaltet die Elemente wie Verweise, datenverbindungen, Ordner und Dateien, die für die Entwicklung benötigten über Projektmappen und Projekte erforderlich sind.  
  
 [Erweitern anderer Teile von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Erklärt, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Services können Sie UI-Elemente erstellen, die die restliche entsprechen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].