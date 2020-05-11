---
title: Erweitern von Eigenschaften | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708419"
---
# <a name="extend-properties"></a>Erweitern von Eigenschaften
Das [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **Fenster Eigenschaften** ist ein universeller Eigenschaftenbrowser für [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] COM- und COM+-Komponenten und unterstützt alle Produkte. Das **Fenster** Eigenschaften `ITypeInfo` arbeitet mit Typinformationen und COM+-Metadaten, um die Entwurfszeiteigenschaften für das aktuell ausgewählte Objekt in einem anderen Fenster in der integrierten Entwicklungsumgebung (IDE) aufzulisten.

 Das **Eigenschaftenfenster,** das durch Drücken von **F4** auf der Tastatur oder auswählen von **Eigenschaftenfenster** im Menü **Ansicht** geöffnet werden kann, wird zum Anzeigen und Bearbeiten konfigurationsunabhängiger, entwurfszeitlicher Eigenschaften und Ereignisse ausgewählter Objekte verwendet. Konfigurationsabhängige Eigenschaften, die Projektlösungen und Projekten zugeordnet sind, werden auf [Eigenschaftenseiten](../../extensibility/internals/property-pages.md)angezeigt. Weitere Informationen finden Sie unter Verwalten von [Konfigurationsoptionen](../../extensibility/internals/managing-configuration-options.md).

 ![Eigenschaftenfensterübersicht](../../extensibility/internals/media/vspropertieswindow.png "vsPropertiesWindow") Eigenschaftenfenster

 Dieser Abschnitt enthält detaillierte Informationen zu den einzelnen Bereichen des **Eigenschaftenfensters** und den Schnittstellen, die Sie implementieren und aufrufen müssen, um das Fenster aufzufüllen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Eigenschaftenfensterübersicht](../../extensibility/internals/properties-window-overview.md)

 Erläutert den Zweck des **Eigenschaftenfensters** relativ zum Werkzeugfenster und zum Dokumentfenster.

- [Vorlagenrichtlinie und das Eigenschaftenfenster](../../extensibility/internals/template-policy-and-the-properties-window.md)

 Erläutert, wie ein Projekt in einem Enterprise-Vorlagenprojekt enthalten ist und wie dieses Enterprise-Vorlagenprojekt Richtlinien erzwingen kann.

- [Eigenschaften Fensterfelder und Schnittstellen](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 Erläutert die Auswahlgrundlage, die bestimmt, welche Informationen im **Eigenschaftenfenster** angezeigt werden.

- [Eigenschaftenfenster-Objektliste](../../extensibility/internals/properties-window-object-list.md)

 Beschreibt den Zweck der **Objektliste** Eigenschaftenfenster und beschreibt, wie die Umgebung darüber informiert wird, dass ein neues Objekt ausgewählt wurde, wenn ein anderes Objekt aus dieser Liste einen Aufruf auslöst.

- [Eigenschaftenfensterschaltflächen](../../extensibility/internals/properties-window-buttons.md)

 Erläutert den Zweck der vier Standardschaltflächen, **die** auf der Symbolleiste eigenschaften angezeigt werden.

- [Eigenschaften-Anzeigeraster](../../extensibility/internals/properties-display-grid.md)

 Erläutert, wo sich die Felder für Eigenschaftsnamen und Eigenschaftswerte im Raster befinden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Projekttypen](../../extensibility/internals/project-types.md)

 Erläutert Projekte als Bausteine [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] der IDE.

- [Kompilieren und Erstellen](../../ide/compiling-and-building-in-visual-studio.md)

 Beschreibt, wie Sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] die Plattform zum kontinuierlichen Testen und Debuggen von Anwendungen beim Erstellen verwenden können.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 Beschreibt `IDispatch` die Schnittstelle, die zuerst entwickelt wurde, um die Automatisierung zu unterstützen, und stellt einen spät gebundenen Mechanismus für den Zugriff auf und das Abrufen von Informationen über die Methoden und Eigenschaften eines Objekts bereit.

- [Verwalten von Anwendungseinstellungen (.NET)](../../ide/managing-application-settings-dotnet.md)

 Bietet eine Übersicht über die Anwendungseinstellungen, mit denen Sie Ihre Anwendung so konfigurieren können, dass Eigenschaftswerte in einer externen Konfigurationsdatei anstelle des kompilierten Codes der Anwendung gespeichert werden.

- [Projektmappen und Projekte](../../ide/solutions-and-projects-in-visual-studio.md)

 Erläutert, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] wie die Elemente wie Verweise, Datenverbindungen, Ordner und Dateien, die für Ihre Entwicklung durch Lösungen und Projekte erforderlich sind, effizient verwaltet werden.

- [Erweitern anderer Teile von Visual Studio](../../extensibility/extending-other-parts-of-visual-studio.md)

 Erläutert, wie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]-Komponenten passen.
