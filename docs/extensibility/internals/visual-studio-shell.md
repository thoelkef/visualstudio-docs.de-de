---
title: "Visual Studio Shell | Microsoft Docs"
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
  - "Visual Studio-Shell"
  - "Visual Studio shell"
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Visual Studio Shell
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ist der primäre Agent Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die Shell stellt die notwendige Funktionalität zum Aktivieren von VSPackages, gemeinsame Dienste zu verwenden. Da die Architektur Ziel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden primäre Funktionalität steht Ihnen in den VSPackages zu die Shell ist ein Framework Grundfunktionen und support als auch die Kommunikation zwischen der Komponente VSPackages.  
  
## Shell\-Aufgaben  
 Die Shell hat folgende wichtigsten Aufgaben:  
  
-   Unterstützung von grundlegenden Elemente der Benutzeroberfläche \(UI\) \(über COM\-Schnittstellen\). Dazu gehören Standardmenüs und Symbolleisten, Fensterrahmen Dokument oder mit mehreren Dokumentschnittstelle \(MDI\) untergeordnete Fenster, und Tool Fensterrahmen und andockunterstützung.  
  
-   Warten eine laufende Liste aller geöffneten Dokumente in einer ausgeführten Dokumenttabelle \(RDT\), um die Persistenz von Dokumenten zu koordinieren und sichergestellt, dass dieses eine Dokument auf mehr als eine Art oder auf nicht kompatible Weise geöffnet werden kann.  
  
-   Unterstützt die Schnittstelle\-Befehlsrouting und Befehlsbehandlung `IOleCommandTarget`.  
  
-   Laden von VSPackages zu den entsprechenden Zeitpunkten. Verzögertes Laden eines VSPackages ist erforderlich zur Verbesserung der Leistung der Shell.  
  
-   Verwalten bestimmte gemeinsamer Dienste, wie z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, die grundlegende Shell stellt Funktionen bereit, und <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, die grundlegende Windowing\-Funktionen bereitstellt.  
  
-   Verwalten die Projektmappendateien \(.sln\). Projektmappen enthalten Gruppen von verwandten Projekten, ähnlich wie \(.dsw\)\-Arbeitsbereichsdateien in Visual C\+\+ 6.0.  
  
-   Tracking\-Shell\-Wide\-Auswahl, Kontext und Währung. Die Shell verfolgt die folgenden Elementtypen:  
  
    -   Das aktuelle Projekt  
  
    -   Das aktuelle bzw. die Element\-ID der aktuellen <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   Die aktuelle Auswahl für die **Eigenschaften** Fenster oder `SelectionContainer`  
  
    -   Der UI\-Kontext\-IDs oder CmdUIGuids, die steuern, die Sichtbarkeit der Befehle, Menüs und Symbolleisten  
  
    -   Die derzeit aktiven Elemente, z. B. das aktive Fenster, Dokument und rückgängig\-manager  
  
    -   Der Benutzerkontext\-Attribute, die dynamische Hilfe Laufwerk  
  
 Die Shell vermittelt auch die Kommunikation zwischen den installierten VSPackages und Dienste. Es unterstützt die Kernfunktionen der Shell und stellt sie zur Verfügung, die alle integrierten VSPackages [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Diese Kernfunktionen gehören die folgenden Elemente:  
  
-   **Zur** Dialogfeld Box und Splash\-Bildschirm  
  
-   **Neu hinzufügen "und" Vorhandenes Element hinzufügen** Dialogfelder  
  
-   **Klassenansicht** Fenster und **Objektkatalog**  
  
-   **Verweise** \(Dialogfeld\)  
  
-   **Dokumentgliederung** Fenster  
  
-   **Dynamische Hilfe** Fenster  
  
-   **Suchen** und **Ersetzen**  
  
-   **Projekt öffnen** und **geöffnete Datei** Dialogfelder in der **Neu** Menü  
  
-   **Optionen** im Dialogfeld auf die **Tools** Menü  
  
-   **Eigenschaften** Fenster  
  
-   **Projektmappen\-Explorer**  
  
-   **Aufgabenliste** Fenster  
  
-   **Toolbox**  
  
## Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)