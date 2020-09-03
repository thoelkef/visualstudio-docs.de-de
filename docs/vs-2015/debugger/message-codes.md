---
title: Meldungscodes | Microsoft-Dokumentation
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182960"
---
# <a name="message-codes"></a>Meldungscodes
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Jede Meldungszeile, die in der [Meldungsansicht](../debugger/messages-view.md) angezeigt wird, enthält den Code „P“, „S“, „s“ oder „R“. Diese Codes haben folgende Bedeutung:  
  
|Code|Bedeutung|  
|----------|-------------|  
|P|Die Meldung wurde mit der Funktion **PostMessage** an die Warteschlange gesendet. Zur endgültigen Disposition der Meldung sind keine Informationen verfügbar.|  
|S|Die Meldung wurde mit der Funktion **SendMessage** gesendet. Dies bedeutet, dass der Absender die Kontrolle erst wiedererlangt, wenn der Empfänger die Meldung verarbeitet und zurückgibt. Der Empfänger kann daher einen Rückgabewert an den Absender zurückgeben.|  
|s|Die Meldung wurde zwar gesendet, doch verhindert die Sicherheit den Zugriff auf den Rückgabewert.|  
|R|Jede Zeile mit dem Code „S“ verfügt über eine entsprechende Zeile mit dem Code „R“ (Rückgabe), die den Rückgabewert der Meldung enthält. Manchmal sind Meldungsaufrufe geschachtelt. Das bedeutet, dass ein Meldungshandler eine weitere Nachricht sendet.|
