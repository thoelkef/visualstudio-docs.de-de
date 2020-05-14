---
title: Meldungscodes | Microsoft-Dokumentation
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
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62846272"
---
# <a name="message-codes"></a>Meldungscodes
Jede Meldungszeile, die in der [Meldungsansicht](../debugger/messages-view.md) angezeigt wird, enthält den Code „P“, „S“, „s“ oder „R“. Diese Codes haben folgende Bedeutung:

|Code|Bedeutung|
|----------|-------------|
|P|Die Meldung wurde mit der Funktion **PostMessage** an die Warteschlange gesendet. Zur endgültigen Disposition der Meldung sind keine Informationen verfügbar.|
|S|Die Meldung wurde mit der Funktion **SendMessage** gesendet. Dies bedeutet, dass der Absender die Kontrolle erst wiedererlangt, wenn der Empfänger die Meldung verarbeitet und zurückgibt. Der Empfänger kann daher einen Rückgabewert an den Absender zurückgeben.|
|s|Die Meldung wurde zwar gesendet, doch verhindert die Sicherheit den Zugriff auf den Rückgabewert.|
|R|Jede Zeile mit dem Code „S“ verfügt über eine entsprechende Zeile mit dem Code „R“ (Rückgabe), die den Rückgabewert der Meldung enthält. Manchmal sind Meldungsaufrufe geschachtelt. Das bedeutet, dass ein Meldungshandler eine weitere Nachricht sendet.|