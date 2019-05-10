---
title: Message-Codes | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 92cc911b0217a406302553b3d913c032fc915b4c
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58961706"
---
# <a name="message-codes"></a>Meldungscodes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält ein 'P', des, ",' oder 'R'-Code. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Nachricht gesendet wurde, an die Warteschlange mit der **PostMessage** Funktion. Keine Informationen sind verfügbar, über die endgültige Anordnung der Nachricht.|  
|S|Die Nachricht gesendet wurde, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und gibt die Meldung zurück. Der Empfänger kann daher einen Rückgabewert zurück an dem Absender übergeben.|  
|s|Die Nachricht gesendet wurde, aber die Sicherheit wird verhindert, dass es sich bei den Zugriff auf den Rückgabewert.|  
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, in der Rückgabewert der Meldung aufgeführt. Manchmal werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht über einen anderen Nachrichtentyp versendet.|
