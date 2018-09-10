---
title: Erweitern von Eigenschaften | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 77b5861dd084098e561f3642b5738dd0279d4b52
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2018
ms.locfileid: "39512108"
---
# <a name="extend-properties"></a>Erweitern von Eigenschaften
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Eigenschaften** Fenster ist eine universelle Eigenschaftenbrowser für COM- und COM+-Komponenten und unterstützt alle [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Produkte. Die **Eigenschaften** Fenster arbeitet mit `ITypeInfo` geben Informationen und COM+-Metadaten zum Auflisten der Eigenschaften zur Entwurfszeit für das aktuell ausgewählte Objekt in einem anderen Fenster in der integrierten Entwicklungsumgebung (IDE).  
  
 Die **Eigenschaften** Fenster, das durch Drücken von geöffnet werden kann **F4** auf der Tastatur, oder wählen Sie **Fenster "Eigenschaften"** auf die **Ansicht** im Menü Dient zum Anzeigen und Bearbeiten der Konfiguration unabhängig, zur Entwurfszeit Eigenschaften und Ereignissen ausgewählter Objekte. Konfigurationsabhängigen Eigenschaften für Projektmappen und Projekten, werden angezeigt, auf [Eigenschaftenseiten](../../extensibility/internals/property-pages.md). Weitere Informationen [verwalten Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).  
  
 ![Übersicht über das Eigenschaftenfenster](../../extensibility/internals/media/vspropertieswindow.png "VsPropertiesWindow")  
Eigenschaftenfenster  
  
 Dieser Abschnitt enthält ausführliche Informationen zu den einzelnen Bereichen im Zusammenhang der **Eigenschaften** Fenster und die Schnittstellen, die Sie implementieren müssen, und Aufruf an das Fenster zu füllen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht über das Eigenschaftenfenster](../../extensibility/internals/properties-window-overview.md)  
 Erläutert den Zweck der **Eigenschaften** Fensters in Bezug auf das Toolfenster und Dokumentfenster.  
  
 [Vorlagenrichtlinie und das Fenster "Eigenschaften"](../../extensibility/internals/template-policy-and-the-properties-window.md)  
 Erläutert, wie ein Projekt in einem Enterprise-Vorlagen-Projekt enthalten ist, und wie diese Enterprise-Vorlagenprojekt Richtlinie erzwingen kann.  
  
 [Eigenschaften im Fenster Felder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md)  
 Erläutert die Grundlage für die Auswahl, die bestimmt, welche Informationen angezeigt werden, in der **Eigenschaften** Fenster.  
  
 [Objektliste des Eigenschaftenfensters](../../extensibility/internals/properties-window-object-list.md)  
 Beschreibt den Zweck der der **Eigenschaften** Objektliste des Eigenschaftenfensters, beschreiben Sie, wenn ein anderes Objekt aus dieser Liste einen Aufruf ausgelöst wird, die Umgebung informiert wird, dass ein neues Objekt ausgewählt wurde.  
  
 [Schaltflächen des Eigenschaftenfensters](../../extensibility/internals/properties-window-buttons.md)  
 Erläutert den Zweck der vier Schaltflächen angezeigt werden, auf die **Eigenschaften** Symbolleiste des Fensters.  
  
 [Anzeigeraster für Eigenschaften](../../extensibility/internals/properties-display-grid.md)  
 Erläutert, in dem die Eigenschaftsnamen und Werte der Eigenschaftenfelder im Raster gefunden werden.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Projekttypen](../../extensibility/internals/project-types.md)  
 Projekte wird erläutert, wie die Bausteine von der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE.  
  
 [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)  
 Beschreibt, wie Sie die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Plattform für die fortlaufend testen und Debuggen von Anwendungen erstellen.  
  
 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)  
 Beschreibt die `IDispatch` -Schnittstelle, die zuerst entwickelt wurde, um Automation, einen spät gebundenen Mechanismus zum zugreifen und Abrufen von Informationen zu den Methoden und Eigenschaften eines Objekts zu unterstützen.  
  
 [Verwalten von Anwendungseinstellungen (.NET)](../../ide/managing-application-settings-dotnet.md)  
 Bietet eine Übersicht über Anwendungseinstellungen, mit denen Sie Ihre Anwendung so konfigurieren, dass Eigenschaftswerte in einer externen Konfigurationsdatei anstelle von kompilierten Code der Anwendung gespeichert sind.  
  
 [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] effizient verwaltet die Elemente wie z. B. Verweise, datenverbindungen, Ordner und Dateien, die von der Entwicklung über Projektmappen und Projekte erforderlich sind.  
  
 [Erweitern von anderen Teilen von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Dienste zum Erstellen von UI-Elemente, die den Rest der entsprechen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].