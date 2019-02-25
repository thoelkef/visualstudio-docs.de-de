---
title: Source-Control-Plug-ins | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a717fdb885669ae4893dc4234c58233dec2957be
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691656"
---
# <a name="source-control-plug-ins"></a>Quellcodeverwaltungs-Plug-Ins
Der Referenzabschnitt Source Control-Plug-in SDK enthält die vollständige Benutzeroberfläche-Spezifikation, mit dem Quellcodeverwaltungs-Systeme integriert werden kann [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Es gibt an, die Syntax und Semantik der verschiedenen Funktionen und Daten, die das Quellcodeverwaltungs-Plug-in implementieren muss, um die Kommunikation mit dem [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] integrierte Entwicklungsumgebung (IDE).

## <a name="in-this-section"></a>In diesem Abschnitt
- [Source-Control-Plug-in-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md) Listet Funktionen auf, die durch das Quellcodeverwaltungs-Plug-in implementiert werden müssen, um die Datenquellen-Plug-in-API entsprechen.

- [Rückruf-Funktionen, die von der IDE implementierte](../extensibility/callback-functions-implemented-by-the-ide.md) beschreibt Funktionen, die das Quellcodeverwaltungs-Plug-in verwendet wird, um zurück zur IDE Informationen übergeben, während bestimmte Befehle ausgeführt werden.

- [Enumeratoren](../extensibility/enumerators.md) Listet die Datentypen der Enumerator in der Quelle Steuerelement-Plug-in-API, die das Quellcodeverwaltungs-Plug-in zu kennen müssen.

- [Funktionsflags](../extensibility/capability-flags.md) beschreibt die `SCC_CAP_xxx` Flags, die Funktionen des Providers angegeben werden.

- [Bitflags, die von bestimmten Befehlen verwendete](../extensibility/bitflags-used-by-specific-commands.md) enthält Flags, die im Kontext der bestimmten Befehle nützlich sind.

- [Fehlercodes](../extensibility/error-codes.md) Listet allgemeine Fehler Rückgabewerte von Funktionen als `SCCTRN`.

- [Wird als Schlüssel für die Suche nach einem Datenquellen-Steuerelement-Plug-in Zeichenfolgen](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) wird beschrieben, die Schlüssel für den Zugriff auf die Registrierung, um das Quellcodeverwaltungs-Plug-in finden.

- [MSSCCPRJ. SCC-Datei](../extensibility/mssccprj-scc-file.md) beschreibt eine clientseitige Datei mit den Informationen, die für die IDE nicht transparent, aber wird, durch das Quellcodeverwaltungs-Plug-in, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen.

- [Bewährte Methoden für die Implementierung einer Datenquellen-Steuerelement-Plug-Ins](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) stellt eine Auflistung von wichtige technische Erinnerungen zu merken, während Sie die Datenquellen-Plug-in-API implementieren.

- [Einschränkungen für Zeichenfolgenlängen](../extensibility/restrictions-on-string-lengths.md) sind Einschränkungen in der Quelle-Plug-in-API für die Längen der Zeichenfolgen, die in verschiedenen Funktionen verwendet.

- [Glossar](../extensibility/source-control-plug-in-glossary.md) bietet nützliche Begriffe und ihre Definitionen für die Source-Control-Plug-in SDK-Dokumentation lesen.

- [Vorgehensweise: Aktivieren Sie Off Kompatibilitätswarnungen für Quellcodeverwaltung-Plug-ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) beschreibt, wie Sie Warnungen zu deaktivieren.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Source-Plug-in-Beispielsteuerelement](https://www.microsoft.com/download/details.aspx?id=55984) enthält ein Beispiel der Quellcodeverwaltungsfunktionen-Plug-in.

- [Testleitfaden für Quellcodeverwaltung-Plug-ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Testverfahren, die im Zusammenhang mit der ein Quellcodeverwaltungs-Plug-In beschreibt.

- [Erstellen ein Datenquellen-Steuerelement-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md) wird erläutert, wie ein Quellcodeverwaltungs-Plug-in erstellen, die Quellcodeverwaltungsfunktionen bereitstellt, während der Verwendung der [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Source Control-Benutzeroberfläche (UI).

- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md) zeigt eine Liste der Themen mit Referenzinformationen.