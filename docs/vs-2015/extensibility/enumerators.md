---
title: Enumeratoren | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 6dcbd3dea8ad932aec5890bc085873ce3d20a8f0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47522797"
---
# <a name="enumerators"></a>Enumeratoren
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Enumeratoren](https://docs.microsoft.com/visualstudio/extensibility/enumerators).  
  
Dieser Abschnitt enthält die Datentypen der Enumerator in der Quelle Steuerelement-Plug-in-API, die das Quellcodeverwaltungs-Plug-in zu kennen müssen.  
  
## <a name="in-this-section"></a>In diesem Abschnitt  
 [Befehlscode](../extensibility/command-code-enumerator.md)  
 Listet die Optionen für die [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) und [SccPopulateList](../extensibility/sccpopulatelist-function.md) Funktionen.  
  
 [Meldung](../extensibility/message-enumerator.md)  
 Listet Flags, die zum Drucken Rückrufs [LPTEXTOUTPROC](../extensibility/lptextoutproc.md).  
  
 [Dateistatuscode](../extensibility/file-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Status einer Datei unter quellcodeverwaltung angeben.  
  
 [Verzeichnisstatuscode](../extensibility/directory-status-code-enumerator.md)  
 Enthält die benannten Konstante Werte, die den Status eines Verzeichnisses in der quellcodeverwaltung angeben.  
  
## <a name="related-sections"></a>Verwandte Abschnitte  
 [Erstellen eines Quellcodeverwaltungs-Plug-Ins](../extensibility/internals/creating-a-source-control-plug-in.md)  
 Die Source-Steuerelement-Plug-in SDK definiert und beschreibt die Ressourcen enthalten.  
  
 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)  
 Fordert den Benutzer für die erweiterten Optionen für den angegebenen Befehl.  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 Untersucht die Liste der Dateien für ihren aktuellen Status an. Darüber hinaus verwendet der `pfnPopulate` Funktion, um den Aufrufer darüber zu benachrichtigen, wenn eine Datei nicht die Kriterien für entspricht der `nCommand`.  
  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 Beschreibt die Callback-Funktion, mit dem [SccOpenProject](../extensibility/sccopenproject-function.md) werden die Nachrichten über das Quellcodeverwaltungs-Plug-in über die IDE angezeigt.  
  
 [Quellcodeverwaltungs-Plug-Ins](../extensibility/source-control-plug-ins.md)  
 Enthält eine vollständige Liste aller Elemente in der Quelle-Plug-in-API.

