---
title: Verwenden von Schriftarten und Farben | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: "27"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0ce64c7cac36319d1e55efb0ddf2216dc218805c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="using-fonts-and-colors"></a>Verwenden von Schriftarten und Farben
Die [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet Unterstützung für die Verwendung von Schriftarten und Farben zum Anzeigen von Text.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Schriftart und Farbe (Übersicht)](../extensibility/font-and-color-overview.md)  
 Erläutert, Schriftart und Farbe Einstellungen für Text in die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung (IDE). Außerdem werden die Konzepte von Kategorien und Elemente anzeigen, und beschreibt, wie VSPackages und die Core-Editor Textattribute verwenden.  
  
 [Abrufen von Informationen zur Schriftart und Farbe für die farbliche Kennzeichnung von Text](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Enthält Richtlinien zum Implementieren von farbliche Kennzeichnung von Text in VSPackages, die verwalten **Kategorien** außer **Text-Editor**.  
  
 [Zugriff auf gespeicherte Schriftart- und Farbeinstellungen](../extensibility/accessing-stored-font-and-color-settings.md)  
 Erläutert, wie die aktuelle Schriftart und Farbe Einstellungen gespeichert, abgerufen und angewendet werden können.  
  
 [Implementieren benutzerdefinierte Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)  
 Beschreibt die grundlegenden Schritte, mit dem ein Fenster erstellen und verwenden eine eigene von **Elemente anzeigen** und **Kategorien** Textanzeige unterstützen.  
  
 Dieser Ansatz erfordert eine VSPackage implementiert die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> Schnittstelle und entsprechende Schnittstellen.  
  
 [Vorgehensweise: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Erläutert das Definieren und registrieren Sie eine Kategorie mit integrierten Schriftarten und Farben, und initiieren die Verwendung von vom System bereitgestellte Schriftarten und Farben.  
  
## <a name="reference"></a>Verweis  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Enthält eine Instanz von der `IVsFontAndColorDefaults` oder <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> Schnittstelle, die ein bestimmtes Element in aufgeführten entspricht, der **Einstellungen anzeigen für** in Liste der **Schriftarten und Farben** auf der Seite der **Optionen** (Dialogfeld).  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Ermöglicht eine VSPackage zur Unterstützung der IDE **Schriftarten und Farben** Seite durch die Definition für ein Fenster oder eine Benutzeroberflächenkomponente Standardschriftarten und Farben.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Stellt einen Mechanismus bereit, mit dem eines VSPackage, das Unterstützung von Schriftart und Farbe kann Geben Sie eine Anzeigeelements - superverbindliche Kategorie, die die Vereinigung der zwei oder mehrere Kategorien darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Ermöglicht eine VSPackage, um die Schriftart und Farbe Daten abgerufen werden, oder in der Registrierung speichern.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Benachrichtigt VSPackages, die Schriftart und Farbe Informationen zu Änderungen in Schriftart-und farbeinstellungen verwenden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Bietet Tools zum Arbeiten mit der Eingabe- und Daten, die von den Methoden der verwendet wird die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Schriftart und Farbe** Mechanismus.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Steuert das Zwischenspeichern von Schriftart-und farbeinstellungen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)  
 Beschreibt, wie VSPackages Sprachdienste verwenden können, zum Anpassen der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor.  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries wie die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] -Editor Sprachdienste implementiert Syntaxfarben verwendet.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erklärt, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Services können Sie UI-Elemente erstellen, die die restliche entsprechen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].