---
title: Visual Studio-Befehlstabelle (. Vsct) Dateien | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704024"
---
# <a name="visual-studio-command-table-vsct-files"></a>VSCT-Dateien (Visual Studio Command Table)
Eine Befehlstabellenkonfigurationsdatei ist eine Textdatei, die den Befehlssatz beschreibt, den ein VSPackage enthält. Der [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] VSCT-Compiler (Befehlstabelle) kompiliert XML-basierte Konfigurationsdateien (.vsct-Dateien) in binäre Befehlstabellenausgabedateien (.cto). Die resultierenden .cto-Dateien sind die gleichen wie die Dateien, die mithilfe des Compilers der Befehlstabelle (CTC) erstellt werden, um .ctc-Konfigurationsdateien zu kompilieren. XML-basierte .vsct-Dateien haben jedoch einige Vorteile, z. B. einen XML-Editor und XML IntelliSense.

 Weitere Informationen zur Syntax und Semantik von .vsct-Dateien finden Sie unter Entwerfen der [XML-Befehlstabelle (. Vsct) Dateien](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>In diesem Abschnitt
 [Entwerfen von Dateien für XML-Befehlstabellen (VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Beschreibt das Entwerfen von .vsct-Dateien.

 [Gewusst wie: Erstellen einer VSCT-Datei](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Vergleicht die Methoden zum Erstellen einer .vsct-Datei. Beschreibt den Prozess zum manuellen Erstellen einer neuen .vsct-Datei.

## <a name="related-sections"></a>Verwandte Abschnitte
 [VSCT-XML-Schemareferenz](../../extensibility/vsct-xml-schema-reference.md)

 Enthält Details zu jedem Abschnitt der XML-Konfigurationsdatei der Befehlstabelle.

 [Befehlstabellenkonfiguration (. Ctc) Dateien](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Bietet einen Überblick über das veraltete .ctc-Dateiformat.

 [Hinzufügen von Benutzeroberflächenelementen mit VSPackages](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Beschreibt die Spezifikation des Befehlstabellenformats.

 [Ressourcen in VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Beschreibt die Verwendung verwalteter und nicht verwalteter Ressourcen in verwalteten VSPackages.

 [Befehle, Menüs und Symbolleisten](../../extensibility/internals/commands-menus-and-toolbars.md)

 Erläutert, wie eine Benutzeroberfläche mit Menüs, Symbolleisten und Kombinationsfeldern für Befehle erstellt wird.
