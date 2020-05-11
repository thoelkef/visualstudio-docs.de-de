---
title: Quellcodeverwaltung Plug-Ins | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cc5f092e0ae93109d071af0b1a67999947e73e90
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80699892"
---
# <a name="source-control-plug-ins"></a>Quellcodeverwaltungs-Plug-Ins
Der Abschnitt Source Control Plug-in SDK-Referenz enthält die vollständige Schnittstellenspezifikation, mit der Quellcodeverwaltungssysteme in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]integriert werden können. Es gibt die Syntax und Semantik der verschiedenen Funktionen und Datentypen an, die [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] das Quellcodeverwaltungs-Plug-In implementieren muss, um eine Schnittstelle mit der integrierten Entwicklungsumgebung (IDE) zu ermöglichen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Quellcodeverwaltung Plug-In-API-Funktionen](../extensibility/source-control-plug-in-api-functions.md) Listet Funktionen auf, die vom Quellcodeverwaltungs-Plug-In implementiert werden müssen, um die Quellcodeverwaltungs-Plug-In-API zu erfüllen.

- [Von der IDE implementierte Rückruffunktionen](../extensibility/callback-functions-implemented-by-the-ide.md) Beschreibt Funktionen, die das Quellcodeverwaltungs-Plug-In verwendet, um Informationen an die IDE zurückzugeben, während bestimmte Befehle ausgeführt werden.

- [Enumeratoren](../extensibility/enumerators.md) Listet die Enumeratordatentypen in der Quellcodeverwaltungs-Plug-In-API auf, die das Quellcodeverwaltungs-Plug-In kennen muss.

- [Fähigkeitsflags](../extensibility/capability-flags.md) Beschreibt `SCC_CAP_xxx` die Flags, die auf die Funktionen eines Anbieters hinweisen.

- [Bitflags, die von bestimmten Befehlen verwendet werden](../extensibility/bitflags-used-by-specific-commands.md) Listet Flags auf, die im Kontext bestimmter Befehle nützlich sind.

- [Fehlercodes](../extensibility/error-codes.md) Listet allgemeine Fehlerwerte auf, die von Funktionen als `SCCTRN`zurückgegeben werden.

- [Zeichenfolgen, die als Schlüssel zum Suchen eines Quellcodeverwaltungs-Plug-Ins verwendet](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md) werden Beschreibt Schlüssel für den Zugriff auf die Registrierung, um das Quellcodeverwaltungs-Plug-In zu finden.

- [MSSCCPRJ. SCC-Datei](../extensibility/mssccprj-scc-file.md) Beschreibt eine clientseitige Datei, die Informationen enthält, die für die IDE undurchsichtig sind, aber vom Quellcodeverwaltungs-Plug-In verwendet wird, um die Projektmappe oder das Projekt in der Versionskontrolle zu suchen.

- [Bewährte Methoden zum Implementieren eines Quellcodeverwaltungs-Plug-Ins](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md) Enthält eine Sammlung wichtiger technischer Erinnerungen, die Sie sich beim Implementieren der Quellcodeverwaltungs-Plug-In-API merken sollten.

- [Einschränkungen für Zeichenfolgenlängen](../extensibility/restrictions-on-string-lengths.md) Beschreibt Einschränkungen in der Quellcodeverwaltungs-Plug-In-API für die Längen von Zeichenfolgen, die in verschiedenen Funktionen verwendet werden.

- [Glossar](../extensibility/source-control-plug-in-glossary.md) Enthält hilfreiche Begriffe und deren Definitionen zum Lesen der Source Control Plug-In-SDK-Dokumentation.

- [Gewusst wie: Deaktivieren von Kompatibilitätswarnungen für Quellcodeverwaltungs-Plug-Ins](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md) Beschreibt, wie Warnungen deaktiviert werden.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Quellcodeverwaltungs-Plug-In-Beispiel](https://www.microsoft.com/download/details.aspx?id=55984) Stellt ein Beispiel für die Plug-In-Funktionalität der Quellcodeverwaltung bereit.

- [Testhandbuch für Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/test-guide-for-source-control-plug-ins.md) Beschreibt Testverfahren im Zusammenhang mit einem Quellcodeverwaltungs-Plug-In.

- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md) Erläutert, wie Sie ein Quellcodeverwaltungs-Plug-In erstellen, das [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Quellcodeverwaltungsfunktionen bereitstellt, während Sie die Quellcodeverwaltungsbenutzeroberfläche (UI) verwenden.

- [Visual Studio SDK-Referenz](../extensibility/visual-studio-sdk-reference.md) Stellt eine Liste der Referenzthemen vor.
