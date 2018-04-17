---
title: Von der IDE implementiert Rückruffunktionen | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: ffdcc7d92770f486f9a345acf14e12e14214a2b1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="callback-functions-implemented-by-the-ide"></a>Rückruffunktionen implementiert, die von der IDE
Stellen Sie die Integration mit der integrierten Entwicklungsumgebung (IDE) als eine nahtlose möglichst und eine einheitliche benutzererfahrung das Quellsteuerelement-Plug-in Rückruffunktionen können, die von der IDE implementiert werden. Das plug-in kann diese Funktionen zu geeigneten Zeitpunkten während einer Quelle-Steuerungsvorgang zum Weiterleiten von Informationen an den IDE aufrufen; die IDE können Sie diese Informationen als eingebettete Elemente in der systemeigenen Benutzeroberfläche anzeigen. Der Benutzer hat eine weniger fragmentierte Experience in diesem Szenario als wenn das plug-in eine eigene Benutzeroberfläche beschäftigt.  
  
 Die erforderlichen Header-Datei ist scc.h. Der Standardspeicherort ist \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Es ist auch im Ordner "VSIP" mit dem Datenquellen-Steuerelement-Plug-in Beispiel am \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Rückruffunktion, die vom verwendet [SccOpenProject](../extensibility/sccopenproject-function.md) um Meldungen aus dem Quellsteuerelement-Plug-in über die IDE anzuzeigen.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Beschreibt die Rückruffunktion, die vom verwendet [SccPopulateList](../extensibility/sccpopulatelist-function.md) bei die IDE keinen vollständigen Zugriff auf Informationen, die nur die Datenquellen-Steuerelement-Plug-in, z. B. eine vollständige Liste der Dateien unter Versionskontrolle zur Verfügung steht.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Beschreibt die Rückruffunktion, die von verwendet wird, die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Beschreibt die Rückruffunktion, die von verwendet wird, die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Vorgang.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Beschreibt die Rückruffunktion, die durch einen Aufruf zum Festlegen der [SccSetOption](../extensibility/sccsetoption-function.md) mit der die Datenquellen-Steuerelement-Plug-In für die Kommunkation Namensänderungen zurück, in der IDE.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Öffnet ein Projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Überprüft die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder in Projekten, die in der quellcodeverwaltung sind. Jeder Name Verzeichnis- und Dateinamen, die gefunden wird, eine Rückruffunktion übergeben.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Überprüft die Änderungen des Computernamens, die auf eine Liste von Dateien vorgenommen wurden. Jeder Dateiname wird auf eine Rückruffunktion zusammen mit seinem Änderungsstatus übergeben.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Legt eine Vielzahl von Optionen an. Jede Option beginnt mit `SCC_OPT_xxx` und weist einen eigenen definierten Satz von Werten.  
  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)  
 Beschreibt den Inhalt von der Quelle Steuerelement-Plug-in SDK im Abschnitt "Referenz".