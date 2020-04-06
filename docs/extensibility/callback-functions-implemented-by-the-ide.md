---
title: Von der IDE implementierte Rückruffunktionen | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739889"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Von der IDE implementierte Rückruffunktionen
Um die Integration in die integrierte Entwicklungsumgebung (IDE) so nahtlos wie möglich zu gestalten und eine einheitliche Endbenutzererfahrung zu bieten, kann das Quellcodeverwaltungs-Plug-In Rückruffunktionen verwenden, die von der IDE implementiert werden. Das Plug-In kann diese Funktionen zu geeigneten Zeiten während eines Quellcodeverwaltungsvorgangs aufrufen, um Informationen an die IDE zu übergeben. Die IDE kann diese Informationen dann als eingebettete Elemente in ihrer systemeigenen Benutzeroberfläche anzeigen. Der Benutzer hat in diesem Szenario eine weniger fragmentierte Erfahrung, als wenn das Plug-In eine eigene Benutzeroberfläche verwendet.

 Die erforderliche Headerdatei ist *scc.h*. Der Standardspeicherort ist *"Programmdateien", "VSIP 8.0", "EnvSDK" und "common"\\*( Es befindet sich auch im VSIP-Ordner, der das Quellsteuerungs-Plug-In-Beispiel unter *.Programmdateien, VSIP 8.0, MSSCCI\\*, enthält.

## <a name="in-this-section"></a>In diesem Abschnitt
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) Beschreibt die Rückruffunktion, die von [SccOpenProject](../extensibility/sccopenproject-function.md) zum Anzeigen von Nachrichten aus dem Quellcodeverwaltungs-Plug-In über die IDE verwendet wird.

- [POPLISTFUNC](../extensibility/poplistfunc.md) Beschreibt die Rückruffunktion, die von [SccPopulateList](../extensibility/sccpopulatelist-function.md) verwendet wird, wenn die IDE keinen vollständigen Zugriff auf Informationen hat, die nur für das Quellcodeverwaltungs-Plug-In verfügbar sind, z. B. eine vollständige Liste der Dateien unter Versionskontrolle.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) Beschreibt die Rückruffunktion, die vom [SccQueryChanges-Vorgang](../extensibility/sccquerychanges-function.md) verwendet wird.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) Beschreibt die Rückruffunktion, die vom [SccPopulateDirList-Vorgang](../extensibility/sccpopulatedirlist-function.md) verwendet wird.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) Beschreibt die Rückruffunktion, die durch einen Aufruf der [SccSetOption](../extensibility/sccsetoption-function.md) festgelegt wird, die es dem Quellcodeverwaltungs-Plug-In ermöglicht, Namensänderungen an die IDE zurückzugeben.

## <a name="related-sections"></a>Verwandte Abschnitte
- [SccOpenProject](../extensibility/sccopenproject-function.md) Öffnet ein Projekt.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) Überprüft die Liste der Dateien auf ihren aktuellen Status. Darüber hinaus verwendet `pfnPopulate` die Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht den Kriterien für die `nCommand`entspricht.

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Untersucht eine Liste von Verzeichnissen und Dateien in einem Projekt oder Projekten, die sich unter Quellcodeverwaltung befinden. Jeder gefundene Verzeichnis- und Dateiname wird an eine Rückruffunktion übergeben.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) Untersucht Namensänderungen, die an einer Liste von Dateien vorgenommen wurden. Jeder Dateiname wird zusammen mit seinem Änderungsstatus an eine Rückruffunktion übergeben.

- [SccSetOption](../extensibility/sccsetoption-function.md) Legt eine Vielzahl von Optionen fest. Jede Option `SCC_OPT_xxx` beginnt mit und verfügt über einen eigenen definierten Satz von Werten.

- [Quellcodeverwaltung Plug-Ins](../extensibility/source-control-plug-ins.md) Beschreibt den Inhalt des Referenzabschnitts des Source Control Plug-In SDK.
