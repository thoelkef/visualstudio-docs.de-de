---
title: Enumeratoren | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711856"
---
# <a name="enumerators"></a>Enumeratoren
In diesem Abschnitt werden die Enumeratordatentypen in der Quellcodeverwaltungs-Plug-In-API aufgeführt, die das Quellcodeverwaltungs-Plug-In kennen muss.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Befehlscode](../extensibility/command-code-enumerator.md) Listet die Optionen für die Funktionen [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) auf.

- [Nachricht](../extensibility/message-enumerator.md) Aufzählung von Flags, die für den Druckrückruf [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)verwendet werden.

- [Dateistatuscode](../extensibility/file-status-code-enumerator.md) Enthält benannte Konstantenwerte, die den Status einer Datei unter Quellcodeverwaltung angeben.

- [Verzeichnisstatuscode](../extensibility/directory-status-code-enumerator.md) Enthält benannte Konstantenwerte, die den Status eines Verzeichnisses unter Quellcodeverwaltung angeben.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md) Definiert das Quellcodeverwaltungs-Plug-In-SDK und beschreibt die enthaltenen Ressourcen.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) Fordert den Benutzer auf, erweiterte Optionen für den angegebenen Befehl zu erhalten.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Überprüft die Liste der Dateien auf ihren aktuellen Status. Darüber hinaus verwendet `pfnPopulate` die Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien für die `nCommand`entspricht.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Beschreibt die Rückruffunktion, die von [SccOpenProject](../extensibility/sccopenproject-function.md) zum Anzeigen von Nachrichten aus dem Quellcodeverwaltungs-Plug-In über die IDE verwendet wird.

- [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md) Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-In-API bereit.
