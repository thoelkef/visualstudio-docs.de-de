---
title: Enumeratoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2d3a0876dfd3a9d7b9cc86b18f6e9a6ba3b780d3
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66334498"
---
# <a name="enumerators"></a>Enumeratoren
Dieser Abschnitt enthält die Datentypen der Enumerator in der Quelle Steuerelement-Plug-in-API, die das Quellcodeverwaltungs-Plug-in zu kennen müssen.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Befehl Code](../extensibility/command-code-enumerator.md) Listet die Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) Funktionen.

- [Nachricht](../extensibility/message-enumerator.md) listet Flags, die zum Drucken Rückrufs [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).

- [Statuscode: Datei](../extensibility/file-status-code-enumerator.md) enthält, die mit dem Namen Konstante Werte, die den Status einer Datei unter quellcodeverwaltung angeben.

- [Directory Statuscode](../extensibility/directory-status-code-enumerator.md) enthält, die mit dem Namen Konstante Werte, die den Status eines Verzeichnisses in der quellcodeverwaltung angeben.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen ein Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md) Source Control-Plug-in SDK definiert und beschreibt die Ressourcen enthalten.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) fordert den Benutzer zu erweiterten Optionen für den angegebenen Befehl.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) untersucht die Liste der Dateien für ihren aktuellen Status. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) wird beschrieben, die Callback-Funktion, mit dem [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten über das Quellcodeverwaltungs-Plug-in über die IDE angezeigt.

- [Source-Control-Plug-ins](../extensibility/source-control-plug-ins.md) enthält eine vollständige Liste aller Elemente in der Quelle-Plug-in-API.