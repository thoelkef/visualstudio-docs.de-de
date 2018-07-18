---
title: Nachricht Codes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 25b2061d9f20da8e9c4d5b4f9794f400d638260c
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31474442"
---
# <a name="message-codes"></a>Meldungscodes
Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält 'P' des, "," oder "R"-Code. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Meldung wurde bereitgestellt, in die Warteschlange mit der **PostMessage** Funktion. Es sind keine Informationen verfügbar, die über die endgültige Anordnung der Nachricht.|  
|S|Die Nachricht wurde gesendet, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und die Nachricht zurückgegeben. Der Empfänger kann daher einen Rückgabewert zurück zum Absender übergeben.|  
|s|Die Nachricht wurde gesendet, aber Sicherheit verhindert den Zugriff auf den Rückgabewert.|  
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, die den Rückgabewert der Nachricht enthält. In einigen Fällen werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht einer anderen Nachricht sendet.|