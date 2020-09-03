---
title: Enumeratoren | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711856"
---
# <a name="enumerators"></a>Enumeratoren
In diesem Abschnitt werden die enumeratordatentypen in der Quellcodeverwaltungs-Plug-in-API aufgelistet, über die das Quellcodeverwaltungs-Plug-in informiert sein muss.

## <a name="in-this-section"></a>In diesem Abschnitt
- [Befehls Code](../extensibility/command-code-enumerator.md) Listet die Optionen für die Funktionen [sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) und [sccpopulatelist](../extensibility/sccpopulatelist-function.md) auf.

- [Nachricht](../extensibility/message-enumerator.md) Listet die Flags auf, die für den Druck Rückruf verwendet werden, [lptextoutproc](../extensibility/lptextoutproc.md).

- [Dateistatus Code](../extensibility/file-status-code-enumerator.md) Enthält benannte Konstante Werte, die den Zustand einer Datei in der Quell Code Verwaltung angeben.

- [Verzeichnis Statuscode](../extensibility/directory-status-code-enumerator.md) Enthält benannte Konstante Werte, die den Zustand eines Verzeichnisses unter Quell Code Verwaltung angeben.

## <a name="related-sections"></a>Verwandte Abschnitte
- [Erstellen eines Quellcodeverwaltungs-Plug-ins](../extensibility/internals/creating-a-source-control-plug-in.md) Definiert das Quellcodeverwaltungs-Plug-in-SDK und beschreibt die enthaltenen Ressourcen.

- [Sccgetcommandoptions](../extensibility/sccgetcommandoptions-function.md) Fordert den Benutzer auf, erweiterte Optionen für den angegebenen Befehl zu erhalten.

- [Sccpopulatelist](../extensibility/sccpopulatelist-function.md) Überprüft die Liste der Dateien auf Ihren aktuellen Status. Außerdem verwendet die- `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht mit den Kriterien für übereinstimmt `nCommand` .

- [Lptextoutproc](../extensibility/lptextoutproc.md) Beschreibt die Rückruffunktion, die von [sccopenproject](../extensibility/sccopenproject-function.md) zum Anzeigen von Nachrichten aus dem Quellcodeverwaltungs-Plug-in über die IDE verwendet wird.

- [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md) Stellt eine vollständige Auflistung aller Elemente in der Quellcodeverwaltungs-Plug-in-API bereit.
