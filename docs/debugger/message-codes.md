---
title: Message-Codes | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- message codes
ms.assetid: 9f91f4e2-c1f1-4349-9f11-2fbbf59654be
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c09245056bf7e947985bfa55dc9cc4a3a96b8cf
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 02/22/2019
ms.locfileid: "56681191"
---
# <a name="message-codes"></a>Meldungscodes
Jede Nachricht Befehlszeile im [Ansicht "Nachrichten"](../debugger/messages-view.md) enthält ein 'P', des, ",' oder 'R'-Code. Diese Codes haben folgende Bedeutung:

|Code|Bedeutung|
|----------|-------------|
|P|Die Nachricht gesendet wurde, an die Warteschlange mit der **PostMessage** Funktion. Keine Informationen sind verfügbar, über die endgültige Anordnung der Nachricht.|
|S|Die Nachricht gesendet wurde, mit der **SendMessage** Funktion. Dies bedeutet, dass der Absender die Kontrolle nicht, bis der Empfänger verarbeitet und gibt die Meldung zurück. Der Empfänger kann daher einen Rückgabewert zurück an dem Absender übergeben.|
|s|Die Nachricht gesendet wurde, aber die Sicherheit wird verhindert, dass es sich bei den Zugriff auf den Rückgabewert.|
|R|Jede der "Zeile verfügt über eine entsprechende"R"(Rückgabe)-Zeile, in der Rückgabewert der Meldung aufgeführt. Manchmal werden Aufrufe von Message geschachtelt, was bedeutet, dass dieser Handler eine Nachricht über einen anderen Nachrichtentyp versendet.|