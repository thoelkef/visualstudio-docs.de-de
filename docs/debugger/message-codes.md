---
title: Nachricht Codes | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 432012d897ecc4da508dd2925ac655b8dc9d1416
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="message-codes"></a>Meldungscodes
Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält 'P' des, "," oder "R"-Code. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Meldung wurde bereitgestellt, in die Warteschlange mit der **PostMessage** Funktion. Es sind keine Informationen verfügbar, die über die endgültige Anordnung der Nachricht.|  
|S|Die Nachricht wurde gesendet, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und die Nachricht zurückgegeben. Der Empfänger kann daher einen Rückgabewert zurück zum Absender übergeben.|  
|s|Die Nachricht wurde gesendet, aber Sicherheit verhindert den Zugriff auf den Rückgabewert.|  
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, die den Rückgabewert der Nachricht enthält. In einigen Fällen werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht einer anderen Nachricht sendet.|