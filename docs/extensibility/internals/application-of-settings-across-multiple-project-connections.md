---
title: Anwendung von Einstellungen auf mehrere Projektverbindungen | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 480ccaac58e67a959454e9d4afa9aa57e817c693
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/29/2019
ms.locfileid: "66315842"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>Anwendung von Einstellungen auf mehrere projektverbindungen
Ein Quellcodeverwaltungs-Plug-In können mit der Quelle Steuerelement-Plug-in-API-Version 1.2, erstellt einen Batchvorgang den gleichen Quellcodeverwaltungsvorgang über mehrere Projekte oder mehrere Verbindung Kontexte ausgeführt. Batches können zum Eliminieren Sie redundante projektbezogene Dialogfelder, die von der Benutzeroberfläche verwendet werden.

 Wenn ein Benutzer mehrere Elemente, die mehr als eine Verbindung in ein Quellcodeverwaltungs-Plug-in erstellt wählt, mit der Quelle Steuerelement-Plug-in-API-Version 1.1 (z. B. zwei Webprojekten auf Computern mit verschiedenen Dateifreigabe) angehören, und sie überprüft, erhält der Benutzer die gleiche Dialogfeld Feld wiederholt. Dieses Szenario tritt auf, auch wenn der Benutzer klickt auf die **auf alle anwenden** Kontrollkästchen im Dialogfeld, da die IDE den Zustand für jede Verbindungskontext zurückgesetzt.

## <a name="new-capability-flag"></a>Neue Funktion-flag
 Die `SccBeginBatch` Funktion legt die `SCC_CAP_BATCH` Flags an, dass ein Batchvorgang ausgeführt wird.

## <a name="new-functions"></a>Neue Funktionen
Die folgenden neuen Funktionen unterstützen den Batchvorgang:

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

Die `SCCBeginBatch` Funktion startet eine Gruppe von Quellcodeverwaltungsvorgänge. Die `SccEndBatch` -Funktion schließt die Gruppe. Gruppen können nicht geschachtelt werden.

## <a name="see-also"></a>Siehe auch
- [Neuerungen in der Quelle Steuerelement-Plug-in-API-Version 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)