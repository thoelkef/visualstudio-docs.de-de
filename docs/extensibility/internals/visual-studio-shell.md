---
title: Visual Studio-Shell | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 63b8420b3941114f8edd1e494c8469ae4b81ba79
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ist der primäre Agent der Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die Shell stellt die notwendige Funktionalität zum Aktivieren von VSPackages zu gemeinsamer Dienste gemeinsam nutzen. Da das architektonische Ziel des [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] werden primäre Funktionalität steht Ihnen in der VSPackages, zu die Shell ist ein Framework, die grundlegende Funktionalität und Cross-Kommunikation zwischen der Komponente VSPackages unterstützen.  
  
## <a name="shell-responsibilities"></a>Shell-Aufgaben  
 Die Shell hat folgende wichtigsten Aufgaben:  
  
-   (Über COM-Schnittstellen) unterstützen grundlegende Elemente der Benutzeroberfläche (UI). Dazu gehören Standardmenüs und Symbolleisten, Dokument Fensterrahmen oder mit mehreren Dokumentschnittstelle (MDI) untergeordnete Fenster, und Tool-Fenster-Frames und andockunterstützung.  
  
-   Warten eine laufende Liste aller aktuell geöffneten Dokumente in einer Dokumenttabelle der ausgeführten (RDT) aus, um die Persistenz von Dokumenten zu koordinieren und um sicherzustellen, dass ein Dokument in mehr als eine Möglichkeit, oder auf nicht kompatible Weise geöffnet werden kann.  
  
-   Unterstützt die Schnittstelle-Befehlsrouting und befehlsverarbeitung `IOleCommandTarget`.  
  
-   Laden von VSPackages zu geeigneten Zeitpunkten. Verzögertes Laden eine VSPackage ist notwendig, Verbessern der Leistung der Shell.  
  
-   Verwalten von bestimmte gemeinsame Dienste, z. B. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, das grundlegende Shell-Funktionen bietet und <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, die grundlegende fensterverwaltungsfunktionalität bietet ausgeben.  
  
-   Verwalten die Projektmappendateien (.sln) an. Lösungen werden Gruppen von verwandten Projekten, ähnlich wie (dsw)-Arbeitsbereichsdateien in Visual C++ 6.0 enthalten.  
  
-   Überwachung Shell-Wide-Auswahl, Kontext und Währung. Die Shell verfolgt die folgenden Typen von Elementen:  
  
    -   Das aktuelle Projekt  
  
    -   Die aktuelle Projektelement oder das aktuelle Element-ID<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>  
  
    -   Die aktuelle Auswahl für die **Eigenschaften** Fenster oder`SelectionContainer`  
  
    -   Die UI-Kontext-IDs oder CmdUIGuids, die steuern, die Sichtbarkeit der Befehle, Menüs und Symbolleisten  
  
    -   Die derzeit aktiven Elemente, z. B. das aktive Fenster, Dokument und Rollback-manager  
  
    -   Der Benutzerkontext-Attribute, die dynamische Hilfe Laufwerk  
  
 Die Shell vermittelt auch die Kommunikation zwischen den installierten VSPackages und Dienste. Es unterstützt die zentralen Funktionen der Shell schreibt und Benutzerprozessen zur Verfügung, die alle VSPackages integriert [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Diese grundlegenden Features gehören die folgenden Elemente:  
  
-   **Informationen zu** Dialogfeld Feld und Splash-Bildschirm  
  
-   **Fügen Sie neu und vorhandenes Element hinzufügen** Dialogfelder  
  
-   **Klassenansicht** Fenster und **Objektkatalog**  
  
-   **Verweise** (Dialogfeld)  
  
-   **Dokumentgliederung** Fenster  
  
-   **Dynamische Hilfe** Fenster  
  
-   **Suchen** und **ersetzen**  
  
-   **Projekt öffnen** und **Dateiöffnungsmodus** Dialogfeldern auf die **neu** Menü  
  
-   **Optionen** Dialogfeld auf die **Tools** Menü  
  
-   **Eigenschaften** Fenster  
  
-   **Projektmappen-Explorer**  
  
-   **Aufgabenliste für die** Fenster  
  
-   **Werkzeugkasten**  
  
## <a name="see-also"></a>Siehe auch  
 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>   
 <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>   
 [VSPackages](../../extensibility/internals/vspackages.md)