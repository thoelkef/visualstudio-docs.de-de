---
title: Verwenden von Schriftarten und Farben | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 96abe68838d028c5de9d6d9418e94ba5b46c0f76
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56693411"
---
# <a name="using-fonts-and-colors"></a>Verwenden von Schriftarten und Farben
Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet Unterstützung für die Verwendung von Schriftarten und Farben zum Anzeigen von Text.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md) erläutert Text Schriftart und Farbe-Einstellungen in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Außerdem werden die Konzepte von Kategorien und Elemente anzeigen, und beschreibt, wie VSPackages und die Kern-Editor den Text-Attribute verwenden.

- [Abrufen von Schriftart und Farbinformationen für die farbliche Kennzeichnung Text](../extensibility/getting-font-and-color-information-for-text-colorization.md) enthält Richtlinien zum Implementieren von farbliche Kennzeichnung von Text in VSPackages, die verwalten **Kategorien** außer **Text-Editor**.

- [Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md) Explains wie die aktuelle Einstellungen von Schriftart und Farbe gespeichert werden können, abgerufen und angewendet.

- [Implementieren von benutzerdefinierten Kategorien und Elemente anzeigen](../extensibility/implementing-custom-categories-and-display-items.md) beschreibt die grundlegenden Schritte, mit dem ein Fenster erstellen und verwenden eine eigene von **Elemente anzeigen** und **Kategorien** zur Unterstützung der Textanzeige.

 Dieser Ansatz erfordert ein VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle und verwandten Schnittstellen.

- [Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md) erläutert das Definieren und registrieren eine Kategorie mit integrierten Schriftarten und Farben aus, und initiieren die Verwendung von vom System bereitgestellten Schriftarten und Farben.

## <a name="reference"></a>Referenz
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Stellt eine Instanz der `IVsFontAndColorDefaults` oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, die ein bestimmtes Element in aufgeführten entspricht, der **Einstellungen anzeigen für** Liste der **Schriftarten und Farben** auf der Seite die **Optionen** Dialogfeld.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> Aktiviert ein VSPackage, das die IDE unterstützen **Schriftarten und Farben** Seite durch Definieren von Standardschriftarten und Farben für eine Fenster- oder Benutzeroberflächenkomponente.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Stellt einen Mechanismus bereit, mit dem ein VSPackage, das stellt Schriftart- und farbunterstützung kann angeben, Gruppe: eine extrem Kategorie, die die Gesamtmenge von zwei oder mehr Kategorien darstellt.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Ermöglicht einem VSPackages, Schriftart-und Farbdaten abrufen oder speichern Sie sie in der Registrierung.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> Benachrichtigt VSPackages, die Schriftart und Farbe Informationen zu Änderungen in den Schriftart-und farbeinstellungen verwenden.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities> Bietet Tools zum Arbeiten mit den Eingabe- und Daten, die von den Methoden der dient den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Schriftart- und Farbeinstellungen** Mechanismus.

 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> Steuert das Zwischenspeichern von Schriftart-und farbeinstellungen.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md) erläutert, wie VSPackages Sprachdienste können zum Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.

- [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md) Descries wie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor verwendet Sprachdienste zum Implementieren von Syntaxfarben.

- [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md) erläutert, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Dienste zum Erstellen von UI-Elemente, die den Rest der entsprechen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].