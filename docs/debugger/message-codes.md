---
title: Message-Codes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7c1f568ead3e5862460d4ae4e18e51687737d4a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 01/02/2019
ms.locfileid: "53866295"
---
# <a name="message-codes"></a>Meldungscodes
Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält ein 'P', des, ",' oder 'R'-Code. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Nachricht gesendet wurde, an die Warteschlange mit der **PostMessage** Funktion. Keine Informationen sind verfügbar, über die endgültige Anordnung der Nachricht.|  
|S|Die Nachricht gesendet wurde, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und gibt die Meldung zurück. Der Empfänger kann daher einen Rückgabewert zurück an dem Absender übergeben.|  
|s|Die Nachricht gesendet wurde, aber die Sicherheit wird verhindert, dass es sich bei den Zugriff auf den Rückgabewert.|  
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, in der Rückgabewert der Meldung aufgeführt. Manchmal werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht über einen anderen Nachrichtentyp versendet.|