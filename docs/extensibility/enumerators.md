---
title: Enumeratoren | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 84102435092096b7154a46100e9d857a31537482
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="enumerators"></a>Enumeratoren
Dieser Abschnitt enthält die enumeratordatentypen in der Quelle Steuerelement-Plug-in-API, die die Datenquellen-Steuerelement-Plug-in zu kennen muss.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Befehls-Code](../extensibility/command-code-enumerator.md)  
 Listet die Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) Funktionen.  
  
 [Nachricht](../extensibility/message-enumerator.md)  
 Listet die Flags, die für den Druck Rückruf [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Statuscode "Datei"](../extensibility/file-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Zustand einer Datei unter quellcodeverwaltung angeben.  
  
 [Statuscode "Directory"](../extensibility/directory-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Status eines Verzeichnisses in der quellcodeverwaltung angeben.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Definiert die Quelle Steuerelement-Plug-in SDK und beschreibt die Ressourcen enthalten.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Fordert den Benutzer für die erweiterten Optionen für den angegebenen Befehl.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Überprüft die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer benachrichtigen, wenn eine Datei nicht den Kriterien entsprechen der `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Rückruffunktion, die vom verwendet [SccOpenProject](../extensibility/sccopenproject-function.md) um Meldungen aus dem Quellsteuerelement-Plug-in über die IDE anzuzeigen.  
  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)  
 Bietet eine vollständige Liste aller Elemente in der Quelle Steuerelement-Plug-in-API.