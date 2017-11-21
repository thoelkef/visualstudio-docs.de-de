---
title: Debuggen von f# | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 51eaed204db7b50e75a18dfac104a00546770abc
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="debugging-f"></a>Debuggen von F#
Das Debuggen von F# entspricht mit wenigen Ausnahmen dem Debuggen einer verwalteten Sprache:  
  
-   Die **"Auto"** Fenster zeigt keine F#-Variablen.  
  
-   Bearbeiten und Fortfahren wird für F# nicht unterstützt. Das Bearbeiten von F#-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden. Da Codeänderungen während der Debugsitzung nicht übernommen werden, verursacht das Bearbeiten von F#-Code während des Debuggens einen Konflikt zwischen dem Quellcode und dem gedebuggten Code.  
  
-   Der Debugger erkennt keine F#-Ausdrücke. Übersetzen Sie den Ausdruck in C#-Syntax, um während des F#-Debuggings einen Ausdruck in ein Debuggerfenster oder Dialogfeld einzugeben. Beachten Sie beim Übersetzen eines F#-Ausdrucks in C#, dass C# == als Vergleichsoperator für Gleichheit und F# ein einzelnes = verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)
