---
title: Verwenden von Schriftarten und Farben | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- fonts, controlling in IDE
- IDE, controlling text color and fonts
- Fonts and Colors property page
- font and color control [Visual Studio SDK]
- text, IDE
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 28
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 42ebc9414e3e5bb10f2468ed7f5f4fb4900e4ec6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68177227"
---
# <a name="using-fonts-and-colors"></a>Verwenden von Schriftarten und Farben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)]Bietet Unterstützung für die Verwendung von Schriftarten und Farben zum Anzeigen von Text.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Übersicht: Schriftart und Farben](../extensibility/font-and-color-overview.md)  
 Erläutert die Schriftart-und Farbeinstellungen von Text in der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] integrierten Entwicklungsumgebung (Integrated Development Environment, IDE). Außerdem werden die Konzepte von Kategorien und Anzeigeelementen eingeführt, und es wird beschrieben, wie VSPackages und der Core-Editor Text Attribute verwenden.  
  
 [Erhalten von Informationen zu Schriftart und Farbe für die Textfarbe](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Enthält Richtlinien für die Implementierung von Text Farbgebung in VSPackages, die andere **Kategorien** als **Text-Editor**verwalten.  
  
 [Zugriff auf gespeicherte Einstellungen zu Schriftart und Farbe](../extensibility/accessing-stored-font-and-color-settings.md)  
 Erläutert, wie die aktuellen Schriftart-und Farbeinstellungen gespeichert, abgerufen und angewendet werden können.  
  
 [Implementieren benutzerdefinierter Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)  
 Beschreibt die grundlegenden Schritte, mit denen ein Fenster eine eigene **Anzeigeelemente** und **Kategorien** erstellen und verwenden kann, um die Textanzeige zu unterstützen.  
  
 Diese Vorgehensweise erfordert ein VSPackage, um die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> -Schnittstelle und zugehörige Schnittstellen zu implementieren.  
  
 [Vorgehensweise: Zugriff auf integrierte Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Erläutert, wie eine Kategorie mithilfe integrierter Schriftarten und Farben definiert und registriert wird und wie die Verwendung von vom System bereitgestellten Schriftarten und Farben initiiert wird.  
  
## <a name="reference"></a>Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Stellt eine Instanz der `IVsFontAndColorDefaults` <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup> -Schnittstelle oder der-Schnittstelle bereit, die einem bestimmten Element entspricht, das in der Liste **Einstellungen anzeigen für** auf der Seite **Schriftarten und Farben** des Dialog Felds **Optionen** aufgeführt ist.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Ermöglicht einem VSPackage, die Seite IDE **-Schriftarten und Farben** zu unterstützen, indem Standard Schriftarten und Farben für ein Fenster oder eine Benutzeroberflächen Komponente definiert werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Stellt einen Mechanismus bereit, mit dem ein VSPackage, das Schriftart-und Farbunterstützung bereitstellt, eine Anzeigeelement Gruppe angeben kann. Dies ist eine Super Kategorie, die die Union von zwei oder mehr Kategorien darstellt.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Ermöglicht einem VSPackage, Schriftart-und Farbdaten abzurufen oder in der Registrierung zu speichern.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Benachrichtigt VSPackages, die Schriftart-und Farbinformationen zu Änderungen in den Schriftart-und Farbeinstellungen verwenden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Bietet Tools zum Arbeiten mit den Eingabe-und Ausgabedaten, die von den Methoden des [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Schriftart-und Farb** Mechanismus verwendet werden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Steuert das Zwischenspeichern von Schriftart- und Farbeinstellungen.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Entwickeln eines Legacysprachdiensts](../extensibility/internals/developing-a-legacy-language-service.md)  
 Erläutert, wie VSPackages Sprachdienste zum Anpassen des Editors verwenden können [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Beschreibt, wie der [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Editor Sprachdienste zum Implementieren von Syntax Farben verwendet.  
  
 [Erweitern anderer Teile von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] -Dienste zum Erstellen von Benutzeroberflächenelementen verwendet werden, die zu den übrigen [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]-Komponenten passen.
