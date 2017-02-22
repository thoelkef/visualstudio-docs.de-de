---
title: "Schriftart und Farbe (&#220;bersicht) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Editoren [Visual Studio SDK], Schriftart und Farbe"
  - "Schriftart und Farbe-Steuerelement [Visual Studio SDK] Editoren"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
caps.handback.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
---
# Schriftart und Farbe (&#220;bersicht)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Dieses Thema behandelt Schriftart\- und Farbeinstellungen Text in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\).  Er stellt auch die Konzepte von Kategorien und vor unter Elemente anzeigen und VSPackages und es wird beschrieben, wie die Kernfunktionen des Editors simst Attribute verwenden.  
  
## Die Schriftarten und Farben\-Eigenschaftenseite  
 Sie können Attribute des angezeigten Texts in der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierten Entwicklungsumgebung \(IDE\) durch die **Schriftarten und Farben**\-Eigenschaftenseite verwalten.  Um die **Schriftarten und Farben**\-Eigenschaftenseite, auf dem **Extras** Menü zu suchen, klicken Sie auf **Optionen**.  Erweitern Sie den Eintrag **Umgebung**, und klicken Sie dann auf **Schriftarten und Farben**.  
  
## Kategorien und Anzeigen\-Elemente  
 Schriftarten und Farben werden in **Kategorien** und **Elemente anzeigen**organisiert.  
  
-   **Kategorie** ist ein logischer Container für einige oder funktionaler **Elemente anzeigen**.  
  
     Eine Liste von **Kategorien** befindet sich im **Einstellungen anzeigen für** Dropdown\-Steuerelement der **Schriftarten und Farben**\-Eigenschaftenseite.  
  
-   **Element anzeigen** ist eine klar definierte Text entität z. B. einen Kommentar oder eine Zeichenfolge, die eine Steuerungsstruktur getönt werden soll, wenn diese angezeigt wird.  
  
 Jedes **Element anzeigen** ist eindeutig innerhalb **Kategorie** definiert, das sie enthält.  Infolgedessen kann mehr als ein **KategorieElement anzeigen** mit dem gleichen Namen haben.  
  
## VSPackage\-Steuerelement für Schriftarten und Farben  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] VSPackages zu können:  
  
-   Definieren von Schriftart und Farbe **Kategorien**.  
  
-   Geben Sie die Schriftarten und Farben an, die verwendet werden, um **Elemente anzeigen**darzustellen.  
  
-   Interagieren mit der **Schriftarten und Farben**\-Eigenschaftenseite.  
  
-   Gesamtes mehrere **Kategorien** in Gruppen.  
  
-   Beibehalten von Änderungen in den Standardeinstellungen beibehalten.  
  
 Es gibt zwei Möglichkeiten, Schriftart und [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)]in Farbauswahl zu interagieren.  
  
-   Eine Möglichkeit so genannte *Syntaxfarbe*.  Er wird von VSPackages mit den vorhandenen [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Editor anpassen, um einen Sprachdienst zu implementieren und einen Quellcode\-Editor zu erstellen.  
  
     Nur ein **KategorieText\-Editor**nämlich diesen Mechanismus unterstützt.  
  
-   Eine allgemeine Alternative unterstützt alle weiteren **Kategorien** und Benutzeroberflächenkomponenten außer den Quellcode\-Editor, wenn sie Text anzeigt.  Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## Kern\-Editor\-Text\-Einstellungen  
 Schriftart\- und Farbeinstellungen für den Kern des Editors eines Objekts werden von **Text\-EditorKategorie** Sprachdienst bestimmt, das im **Einstellungen anzeigen für** Dropdown\-Steuerelement der **Schriftarten und Farben**\-Eigenschaftenseite gefunden wird.  
  
 Beim Arbeiten mit Editoren, sollten Sie die spezielle Schriftart und Farbe kontrollmechanismus verwenden, den der Sprachdienst bereitstellt, um die **Text\-Editor** Einstellungen zu steuern und zu erweitern.  Der Mechanismus als *Syntaxfarbe* und stellt zur Verfügung:  
  
-   Eine vereinfachte Möglichkeit zum Verwalten der Schriftarten und Farben aus Elemente anzeigen.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> und <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Ein gut definiert und optimierter Mechanismus zur Farbauftrag.  
  
     Weitere Informationen finden Sie unter <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   Die Möglichkeit für beide verwenden **Text\-EditorKategorie** integrierte Anzeigen von Elementen und sie zu erweitern.  
  
     Weitere Informationen finden Sie unter [Gewusst wie: Verwenden von integrierten Färbbare Elemente](../extensibility/internals/how-to-use-built-in-colorable-items.md) und [Benutzerdefinierte Färbbare Elemente](../extensibility/internals/custom-colorable-items.md).  
  
-   Die automatische Beibehaltung des aktuellen Zustands der integrierten und benutzerdefinierten Anzeige der Elemente **Text\-Editor** Kategorie.  
  
 Weitere Informationen über Syntaxfarbe finden Sie unter [Syntaxfarben in eine Legacy\-Sprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## Siehe auch  
 [Legacy\-Schnittstellen im Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [Syntaxfarben in eine Legacy\-Sprachdienst](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)