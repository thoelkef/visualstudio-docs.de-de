---
title: Nachricht Codes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 96f980570bcbee7a26bf742556379899c0a88436
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="message-codes"></a>Meldungscodes
Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält 'P' des, "," oder "R"-Code. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Meldung wurde bereitgestellt, in die Warteschlange mit der **PostMessage** Funktion. Es sind keine Informationen verfügbar, die über die endgültige Anordnung der Nachricht.|  
|S|Die Nachricht wurde gesendet, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und die Nachricht zurückgegeben. Der Empfänger kann daher einen Rückgabewert zurück zum Absender übergeben.|  
|s|Die Nachricht wurde gesendet, aber Sicherheit verhindert den Zugriff auf den Rückgabewert.|  
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, die den Rückgabewert der Nachricht enthält. In einigen Fällen werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht einer anderen Nachricht sendet.|