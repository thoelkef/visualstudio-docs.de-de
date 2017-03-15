---
title: "Verwenden von Schriftarten und Farben | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Schriftarten, steuern in der IDE"
  - "Steuern der Farbe von Text und Schriftarten-IDE"
  - "Eigenschaftenseite für Schriftarten und Farben"
  - "Schriftart und Farbe-Steuerelement [Visual Studio SDK]"
  - "Text, der IDE"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 27
---
# Verwenden von Schriftarten und Farben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] bietet Unterstützung für die Verwendung von Schriftarten und Farben Anzeigetext.  
  
## In diesem Abschnitt  
 [Schriftart und Farbe \(Übersicht\)](../extensibility/font-and-color-overview.md)  
 Erläutert Schriftart\- und Farbeinstellungen Text in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\).  Enthält außerdem die Konzepte von Kategorien und es wird beschrieben, wie unter Elemente anzeigen und VSPackages und Kern des Editors simst Attribute verwenden.  
  
 [Schriftart und Farbe Informationen für die farbliche Kennzeichnung Text abrufen](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Enthält Richtlinien zum Implementieren von Text in farbauftrags VSPackages die **Kategorien** außer **Text\-Editor**verwalten.  
  
 [Zugriff auf gespeicherte Schriftart\- und Farbschema](../extensibility/accessing-stored-font-and-color-settings.md)  
 Erläutert das aktuelle Schriftart\- und Farbeinstellungen gespeichert sind, abgerufen und angewendet werden können.  
  
 [Implementieren von benutzerdefinierten Kategorien und Anzeigeelemente](../extensibility/implementing-custom-categories-and-display-items.md)  
 Beschreibt die Schritte, durch die ein Fenster erstellt werden kann und ihre eigenen von **Elemente anzeigen** und **Kategorien** Anzeige von Text verwendet, unterstützen.  
  
 Bei dieser Vorgehensweise müssen ein VSPackage, die <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>\-Schnittstelle und die verwandten Schnittstellen zu implementieren.  
  
 [Gewusst wie: Zugriff auf die integrierten Schriftarten und Farbschemas](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Erläutert, wie eine Kategorie definiert und registriert, die mithilfe von integrierten Schriftarten und Farben, und initiiert die Verwendung von vom System bereitgestellten Schriftarten und Farben.  
  
## Referenz  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 Stellt eine Instanz `IVsFontAndColorDefaults` oder der <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>\-Schnittstelle bereit, die auf ein bestimmtes Element entspricht, der in der **Einstellungen anzeigen für** in der Liste **Schriftarten und Farben** Seite des **Optionen** Dialogfeld aufgeführt ist.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Aktiviert ein VSPackage, um die Seite **Schriftarten und Farben** IDE durch die Definition von Standardschriftart und Farben für ein Fenster oder Benutzeroberflächenkomponente zu unterstützen.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Stellt einen Mechanismus bereit, mit dem ein VSPackage, das zur Verfügung stellt, Schriftart und Farbunterstützung eine Gruppe Anzeigen\-Element angeben kann, eine super Kategorie, die die Gesamtmenge zweier darstellt oder mehrere Kategorien.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Aktiviert ein VSPackage, Schriftart und speichert es abgerufen oder Farbdaten in der Registrierung.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Benachrichtigt VSPackages die Schriftart und Farbinformationen über Änderungen an den Schriftart\- und Farbeinstellungen verwenden.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Stellt Tools für die Arbeit mit der Eingabe und Ausgabedaten, die von den Methoden des Mechanismus [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **Schriftart und Farben** verwendet wird.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Steuert das Zwischenspeichern von Schriftart\- und Farbeinstellungen.  
  
## Verwandte Abschnitte  
 [Entwickeln einer Sprache](../extensibility/internals/developing-a-legacy-language-service.md)  
 Erläutert, wie Sprachendienste VSPackages verwendet werden kann, um auf den [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor anpassen.  
  
 [Syntaxfarben in benutzerdefinierten Editoren](../extensibility/syntax-coloring-in-custom-editors.md)  
 Erspäht, wie der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor Sprachendienste verwendet, um Syntaxfarbe zu implementieren.  
  
 [Erweitern von anderen Teilen von Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Erläutert, wie [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Diensten verwendet, um Benutzeroberflächenelemente erstellen, die den Rest der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]übereinstimmen.