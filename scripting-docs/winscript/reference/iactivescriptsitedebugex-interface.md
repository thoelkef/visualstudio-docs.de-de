---
title: IActiveScriptSiteDebugEx-Schnittstelle | Microsoft-Dokumentation
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptSiteDebugEx Interface
ms.assetid: 76869378-1a7b-47bd-8cd0-acc31f91d58d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 605505d101611dfe39835671b042852eab5ca9cb
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/19/2019
ms.locfileid: "58146941"
---
# <a name="iactivescriptsitedebugex-interface"></a>IActiveScriptSiteDebugEx-Schnittstelle

Implementieren Sie diese Schnittstelle zusammen mit den `IActiveScriptSiteDebug` Schnittstelle, wenn Sie einen Host, die Sie erhalten eine Benachrichtigung von einem Laufzeitfehler in einer Anwendung aus, und fügen Sie optional für die Anwendung schreiben für das Debuggen muss. Den prozessbasierten Debugmanager stellt Benachrichtigung über `IActiveScriptDebug` , wenn eine Just-In-Time-Debugger-Skript auf dem Computer gefunden wird. Wenn keine Just-In-Time-Debugger Skript gefunden wird; das PDM stellt Benachrichtigung über `IActiveScriptDebugEx` stattdessen.

Um eine Benachrichtigung über einen Laufzeitfehler zu erhalten, muss Ihr Host behandeln `ActiveScriptSiteDebug::OnScriptErrorDebug`. Basierend auf eine Benutzeraktion, Sie können dann entscheiden, ob die internen Debugger und die Rückgabe anfügen oder das Starten des Debuggers in der OnScriptErrorDebug `pfEnterDebugger` Parameter.

## <a name="methods-in-vtable-order"></a>Methoden in Vtable-Reihenfolge

|Methode|Beschreibung|
|------------|-----------------|
|[IActiveScriptSiteDebugEx::OnCanNotJITScriptErrorDebug](../../winscript/reference/iactivescriptsitedebugex-oncannotjitscripterrordebug.md)|Informiert, dass der Host über einen Laufzeit-Skriptfehler beim Debuggen des Prozesses Manager einen externen Just-in-Time-Debugger nicht gefunden wird.|