---
title: Von der IDE implementierte Rückruffunktionen | Microsoft-Dokumentation
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
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58957421"
---
# <a name="callback-functions-implemented-by-the-ide"></a>Von der IDE implementierte Rückruffunktionen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Um die Integration in die integrierte Entwicklungsumgebung (IDE) als nahtlos wie möglich und eine einheitliche benutzererfahrung, das Quellcodeverwaltungs-Plug-in Rückruffunktionen können, die von der IDE implementiert werden. Das plug-in kann diese Funktionen zu geeigneten Zeitpunkten während einen Quellcodeverwaltungsvorgang Weiterleiten von Informationen an die IDE aufrufen. die IDE kann dann diese Informationen als eingebettete Elemente in der systemeigenen Benutzeroberfläche angezeigt. Der Benutzer hat eine weniger fragmenthaften Erfahrung in diesem Szenario als, wenn das plug-in eine eigene Benutzeroberfläche verwendet.  
  
 Die erforderlichen Header-Datei ist scc.h. Der Standardspeicherort ist \Program Files\VSIP 8.0\EnvSDK\common\inc\\. Es ist auch in der VSIP-Ordner mit dem Datenquellen-Steuerelement-Plug-in Beispiel am \Program Files\VSIP 8.0\MSSCCI\\.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Callback-Funktion, mit dem [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten über das Quellcodeverwaltungs-Plug-in über die IDE angezeigt.  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 Beschreibt die Callback-Funktion, mit dem [SccPopulateList](../extensibility/sccpopulatelist-function.md) bei die IDE keine vollständigen Zugriff auf Informationen, die nur für das Quellcodeverwaltungs-Plug-in, z. B. eine vollständige Liste der Dateien unter Versionskontrolle verfügbar ist.  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 Beschreibt die Callback-Funktion, mit dem die [SccQueryChanges](../extensibility/sccquerychanges-function.md) Vorgang.  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 Beschreibt die Callback-Funktion, mit dem die [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) Vorgang.  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 Beschreibt die Callback-Funktion, die durch einen Aufruf zum Festlegen der [SccSetOption](../extensibility/sccsetoption-function.md) , ermöglicht das Quellcodeverwaltungs-Plug-in, um Änderungen zurück in die IDE zu kommunizieren.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 Öffnet ein Projekt.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Untersucht die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`.  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 Überprüft eine Liste von Verzeichnissen und Dateien in einem Projekt oder die Projekte, die unter quellcodeverwaltung stehen. Jeder Name Verzeichnis- und Dateinamen, die gefunden wird, eine Callback-Funktion übergeben.  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 Überprüft die Änderungen, die eine Liste mit den Dateien vorgenommen wurden. Jeder Dateiname wird an eine Callback-Funktion zusammen mit den Status für Änderungen übergeben.  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 Legt eine Vielzahl von Optionen fest. Jede Option beginnt mit `SCC_OPT_xxx` und verfügt über einen eigenen definierten Satz von Werten.  
  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)  
 Beschreibt den Inhalt der Referenzabschnitt des Datenquellen-Steuerelement-Plug-in SDK an.
