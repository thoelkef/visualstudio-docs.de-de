---
title: Enumeratoren | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e57f11f61a1bcb2372a07e34167ecacd324067c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55037797"
---
# <a name="enumerators"></a>Enumeratoren
Dieser Abschnitt enthält die Datentypen der Enumerator in der Quelle Steuerelement-Plug-in-API, die das Quellcodeverwaltungs-Plug-in zu kennen müssen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Befehlscode](../extensibility/command-code-enumerator.md)  
 Listet die Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) Funktionen.  
  
 [Meldung](../extensibility/message-enumerator.md)  
 Listet Flags, die zum Drucken Rückrufs [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Datei-Statuscode](../extensibility/file-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Status einer Datei unter quellcodeverwaltung angeben.  
  
 [Directory-Statuscode](../extensibility/directory-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Status eines Verzeichnisses in der quellcodeverwaltung angeben.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-in](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Die Source-Steuerelement-Plug-in SDK definiert und beschreibt die Ressourcen enthalten.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Fordert den Benutzer für die erweiterten Optionen für den angegebenen Befehl.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Untersucht die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Callback-Funktion, mit dem [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten über das Quellcodeverwaltungs-Plug-in über die IDE angezeigt.  
  
 [Quellcodeverwaltungs-Plug-ins](../extensibility/source-control-plug-ins.md)  
 Enthält eine vollständige Liste aller Elemente in der Quelle-Plug-in-API.