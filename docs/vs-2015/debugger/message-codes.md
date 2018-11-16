---
title: Message-Codes | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0464042c17a3ed0836b99183dacbe4918823c752
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2018
ms.locfileid: "51724635"
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



