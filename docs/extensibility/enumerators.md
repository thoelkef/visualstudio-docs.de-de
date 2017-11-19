---
title: Enumeratoren | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0b9f71c83d70dc6daca7a3906b784d6babf8dea7
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
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