---
title: Von der IDE implementierte Rückruf Funktionen | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: df2daef11303e85d5fe2d0bf33e3df038081db64
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184534"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Von der IDE implementierte Rückruffunktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Integration mit der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) so nahtlos wie möglich zu gestalten und eine einheitliche Benutzerumgebung bereitzustellen, kann das Quellcodeverwaltungs-Plug-in Rückruf Funktionen verwenden, die von der IDE implementiert werden. Das Plug-in kann diese Funktionen zu geeigneten Zeitpunkten während eines Quell Code Verwaltungs Vorgangs aufzurufen, um Informationen an die IDE zu übergeben. die IDE kann diese Informationen dann als eingebettete Elemente in der nativen Benutzeroberfläche anzeigen. Der Benutzer hat in diesem Szenario weniger Fragmentierung, als wenn das Plug-in eine eigene Benutzeroberfläche eingesetzt hat.  
  
 Die erforderliche Header Datei ist SCC. h. Der Standard Speicherort ist \programme\vsip 8.0 \ envsdk\common\inc \\ . Sie befindet sich auch im VSIP-Ordner mit dem Quellcodeverwaltungs-Plug-in-Beispiel unter "\programme\vsip 8.0 \ MSSCCI" \\ .  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Rückruffunktion, die von [sccopenproject](../extensibility/sccopenproject-function.md) zum Anzeigen von Nachrichten aus dem Quellcodeverwaltungs-Plug-in über die IDE verwendet wird.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Beschreibt die Rückruffunktion, die von [sccpopulatelist](../extensibility/sccpopulatelist-function.md) verwendet wird, wenn die IDE keinen vollständigen Zugriff auf Informationen hat, die nur für das Quellcodeverwaltungs-Plug-in verfügbar sind, z. b. eine vollständige Liste der Dateien, die der Versionskontrolle unterliegen.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Beschreibt die Rückruffunktion, die vom [sccquerychanges](../extensibility/sccquerychanges-function.md) -Vorgang verwendet wird.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Beschreibt die Rückruffunktion, die vom [sccpopulatedirlist](../extensibility/sccpopulatedirlist-function.md) -Vorgang verwendet wird.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Beschreibt die Rückruffunktion, die durch einen [csetoption](../extensibility/sccsetoption-function.md) -Aufrufs festgelegt wird, der dem Quellcodeverwaltungs-Plug-in das Übermitteln von Namensänderungen an die IDE ermöglicht.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Öffnet ein Projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Überprüft die Liste der Dateien auf Ihren aktuellen Status. Außerdem verwendet die- `pfnPopulate` Funktion, um den Aufrufer zu benachrichtigen, wenn eine Datei nicht mit den Kriterien für übereinstimmt `nCommand` .  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die der Quell Code Verwaltung unterliegen. Alle gefundenen Verzeichnis-und Dateinamen werden an eine Rückruffunktion übermittelt.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Untersucht Namensänderungen, die an einer Liste von Dateien vorgenommen wurden. Jeder Dateiname wird mit seinem Änderungs Status an eine Rückruffunktion übermittelt.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Legt eine Vielzahl von Optionen fest. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.  
  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)  
 Beschreibt den Inhalt des Referenz Abschnitts des SDK für das Quellcodeverwaltungs-Plug-in.
