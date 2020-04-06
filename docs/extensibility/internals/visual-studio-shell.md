---
title: Visual Studio-Shell | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- shell, Visual Studio
- Visual Studio, shell
ms.assetid: cb124ef4-1a6b-4bfe-bfbf-295ef9c07f36
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fb89fc3b82dc7f142714608d8a669e368216c729
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704001"
---
# <a name="visual-studio-shell"></a>Visual Studio Shell
Die [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Shell ist der primäre [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]Agent der Integration in . Die Shell bietet die erforderliche Funktionalität, damit VSPackages gemeinsame Dienste gemeinsam nutzen kann. Da das architektonische [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Ziel darin besteht, die primäre Funktionalität in den VSPackages zu aktivieren, ist die Shell ein Framework, um grundlegende Funktionen bereitzustellen und die Kreuzkommunikation zwischen der Komponente VSPackages zu unterstützen.

## <a name="shell-responsibilities"></a>Shell-Verantwortlichkeiten
 Die Shell hat die folgenden Hauptaufgaben:

- Unterstützung (über COM-Schnittstellen) grundlegender Elemente der Benutzeroberfläche (UI). Dazu gehören Standardmenüs und Symbolleisten, Dokumentfensterrahmen oder MDI-Fenster (Multi Document Interface) sowie Werkzeugfensterrahmen sowie Dockingunterstützung.

- Verwalten einer laufenden Liste aller derzeit geöffneten Dokumente in einer laufenden Dokumenttabelle (RDT), um die Persistenz von Dokumenten zu koordinieren und sicherzustellen, dass ein Dokument nicht auf mehrere Oder in kompatible Weise geöffnet werden kann.

- Unterstützung der Befehlsrouting- und `IOleCommandTarget`Befehlsbehandlungsschnittstelle , .

- VSPackages zu geeigneten Zeiten laden. Das Verzögern eines VSPackage ist notwendig, um die Leistung der Shell zu verbessern.

- Verwalten bestimmter gemeinsam genutzter Dienste, z. <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell> <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>B. , das grundlegende Shellfunktionen bereitstellt, und , die grundlegende Fensterfunktionen bereitstellt.

- Verwalten der Lösungsdateien (.sln). Lösungen enthalten Gruppen verwandter Projekte, ähnlich wie Workspace-Dateien (.dsw) in Visual C++ 6.0.

- Nachverfolgen der shellweiten Auswahl, des Kontexts und der Währung. Die Shell verfolgt die folgenden Elementtypen:

  - Das aktuelle Projekt

  - Das aktuelle Projektelement oder die ItemID<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>

  - Die aktuelle Auswahl für das **Eigenschaftenfenster** oder`SelectionContainer`

  - Die UI-Kontext-IDs oder CmdUIGuids, die die Sichtbarkeit von Befehlen, Menüs und Symbolleisten steuern

  - Die aktuell aktiven Elemente wie das aktive Fenster, Dokument und Rückgängig-Manager

  - Die Benutzerkontextattribute, die die dynamische Hilfe unterstützen

  Die Shell vermittelt auch die Kommunikation zwischen installierten VSPackages und aktuellen Diensten. Es unterstützt die Kernfunktionen der Shell und stellt sie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]allen in . Zu diesen Kernfunktionen gehören die folgenden Elemente:

- **Informationen** zum Dialogfeld und zum Begrüßungsbildschirm

- **Hinzufügen neuer und Hinzufügen vorhandener** Element-Dialogfelder

- **Klassenansichtsfenster** und **Objektbrowser**

- **Dialogfeld Referenzen**

- **Dokumentumgliederungsfenster**

- **Dynamisches Hilfefenster**

- **Suchen** und **Ersetzen**

- **Öffnen der** Dialogfelder Projekt und **Datei öffnen** im Menü **Neu**

- **Dialogfeld Optionen** im Menü **Extras**

- **Eigenschaftenfenster**

- **Projektmappen-Explorer**

- **Aufgabenlistenfenster**

- **Werkzeugkasten**

## <a name="see-also"></a>Weitere Informationen
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsShell>
- <xref:Microsoft.VisualStudio.Shell.Interop.SVsUIShell>
- [VSPackages](../../extensibility/internals/vspackages.md)
