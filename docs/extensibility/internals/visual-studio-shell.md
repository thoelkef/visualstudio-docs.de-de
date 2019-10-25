---
title: Visual Studio Shell | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60aa48da701857508f9b6fd7fc3d9d0c0603046e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722059"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ist der primäre Agent der Integration in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Die Shell stellt die erforderliche Funktionalität bereit, damit VSPackages gemeinsame Dienste gemeinsam verwenden können. Da das architektonische Ziel von [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] darin besteht, die primäre Funktionalität in den VSPackages zu schützen, ist die Shell ein Framework, um grundlegende Funktionen bereitzustellen und die Kommunikation zwischen den Komponenten-VSPackages zu unterstützen.

## <a name="shell-responsibilities"></a>Shellzuständigkeiten
 Die Shell besteht aus den folgenden Hauptaufgaben:

- Unterstützende (über COM-Schnittstellen) grundlegende Elemente der Benutzeroberfläche (UI). Hierzu gehören Standardmenüs und Symbolleisten, Dokument Fensterrahmen oder untergeordnete MDI-Fenster (multidocument Interface) sowie Tool Fensterrahmen und Andock Unterstützung.

- Verwalten einer Liste aller gegenwärtig geöffneten Dokumente in einer laufenden dokumententabelle (RDT), um die Persistenz von Dokumenten zu koordinieren und sicherzustellen, dass ein Dokument nicht auf mehr als eine Weise geöffnet werden kann, oder auf nicht kompatible Weise.

- Unterstützung der Befehls-und Befehls Bearbeitungs Schnittstelle, `IOleCommandTarget`.

- VSPackages werden zu den richtigen Zeitpunkten geladen. Das verzögerte Laden eines VSPackages ist erforderlich, um die Leistung der Shell zu verbessern.

- Verwaltung bestimmter gemeinsamer Dienste, wie z. b. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>, das grundlegende Shellfunktionen bereitstellt, und <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>, das grundlegende Fenster Funktionen bereitstellt.

- Verwalten der Projektmappendateien (. sln). Lösungen enthalten Gruppen verwandter Projekte, ähnlich wie Arbeitsbereichs Dateien (. DSW) in Visual C++ 6,0.

- Nachverfolgen der shellweiten Auswahl, des Kontexts und der Währung. Die Shell verfolgt die folgenden Elementtypen:

  - Das aktuelle Projekt

  - Das aktuelle Projekt Element oder die aktuelle <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> Itemid.

  - Die aktuelle Auswahl für das **Eigenschaften** Fenster oder `SelectionContainer`

  - Die UI-Kontext-IDs oder cmduiguids, die die Sichtbarkeit von Befehlen, Menüs und Symbolleisten steuern

  - Die derzeit aktiven Elemente, z. b. aktives Fenster, Dokument und rückgängig-Manager

  - Die Benutzer Kontext Attribute, die dynamische Hilfe Steuern

  Die Shell vermittelt auch die Kommunikation zwischen installierten VSPackages und aktuellen Diensten. Es unterstützt die Kernfunktionen der Shell und stellt diese für alle in [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] integrierten VSPackages zur Verfügung. Zu diesen Kern Features zählen die folgenden Elemente:

- Info **-Dialogfeld** und Begrüßungsbildschirm

- **Neue Dialogfelder hinzufügen und vorhandenes Element hinzufügen**

- **Klassenansicht** Fenster und **Objektkatalog**

- **Verweise** (Dialogfeld)

- **Dokument** Gliederungs Fenster

- Fenster " **Dynamische Hilfe** "

- **Suchen** und **ersetzen**

- Dialogfelder " **Projekt öffnen** " und " **Datei öffnen** " im Menü " **neu** "

- Dialogfeld " **Optionen** " **im Menü "** Extras"

- **Eigenschaftenfenster**

- **Projektmappen-Explorer**

- **Aufgabenliste** Fenster

- **Werkzeugpalette**

## <a name="see-also"></a>Siehe auch
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)