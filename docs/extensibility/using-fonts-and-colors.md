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
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b1b4f5b8108ff4027f936abe094efe41647719a7
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53941231"
---
# <a name="using-fonts-and-colors"></a>Verwenden von Schriftarten und Farben
Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet Unterstützung für die Verwendung von Schriftarten und Farben zum Anzeigen von Text.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht: Schriftart und Farben](../extensibility/font-and-color-overview.md)  
 Erläutert, Text-Schriftart und Farbe Einstellungen in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE). Außerdem werden die Konzepte von Kategorien und Elemente anzeigen, und beschreibt, wie VSPackages und die Kern-Editor den Text-Attribute verwenden.  
  
 [Erhalten von Informationen zu Schriftart und Farbe für die Textfarbe](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Enthält Richtlinien zum Implementieren von farbliche Kennzeichnung von Text in VSPackages, die verwalten **Kategorien** außer **Text-Editor**.  
  
 [Zugriff auf gespeicherte Einstellungen zu Schriftart und Farbe](../extensibility/accessing-stored-font-and-color-settings.md)  
 Erläutert, wie die aktuelle Schriftart und Farbe Einstellungen gespeichert, abgerufen und angewendet werden können.  
  
 [Implementieren benutzerdefinierter Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)  
 Beschreibt die grundlegenden Schritte, mit dem ein Fenster erstellen und verwenden eine eigene von **Elemente anzeigen** und **Kategorien** zur Unterstützung der Textanzeige.  
  
 Dieser Ansatz erfordert ein VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle und verwandten Schnittstellen.  
  
 [Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Erläutert das Definieren und registrieren eine Kategorie mit integrierten Schriftarten und Farben aus, und initiieren die Verwendung von vom System bereitgestellten Schriftarten und Farben.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Stellt eine Instanz der `IVsFontAndColorDefaults` oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, die ein bestimmtes Element in aufgeführten entspricht, der **Einstellungen anzeigen für** Liste der **Schriftarten und Farben** auf der Seite die **Optionen** Dialogfeld.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Aktiviert ein VSPackage, das die IDE unterstützen **Schriftarten und Farben** Seite durch Definieren von Standardschriftarten und Farben für eine Fenster- oder Benutzeroberflächenkomponente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Stellt einen Mechanismus bereit, mit dem ein VSPackage, das stellt Schriftart- und farbunterstützung kann angeben, Gruppe: eine extrem Kategorie, die die Gesamtmenge von zwei oder mehr Kategorien darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Ermöglicht einem VSPackages, Schriftart-und Farbdaten abrufen oder speichern Sie sie in der Registrierung.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Benachrichtigt VSPackages, die Schriftart und Farbe Informationen zu Änderungen in den Schriftart-und farbeinstellungen verwenden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Bietet Tools zum Arbeiten mit den Eingabe- und Daten, die von den Methoden der dient den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Schriftart- und Farbeinstellungen** Mechanismus.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Steuert das Zwischenspeichern von Schriftart-und farbeinstellungen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)  
 Erläutert, wie VSPackages Sprachdienste können zum Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries wie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor verwendet Sprachdienste zum Implementieren von Syntaxfarben.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]-Komponenten passen.