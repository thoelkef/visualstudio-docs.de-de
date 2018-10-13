---
title: Debuggen [F#] | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Debugging [F#]
- F#, debugging
ms.assetid: 20bcd51c-2d06-4281-9a1e-ef2b91d1a779
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: dd722e40a0579181e3c361706f0775aaf350c341
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49209572"
---
# <a name="debugging-f"></a>Debuggen von F# #
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Das Debuggen von F# entspricht mit wenigen Ausnahmen dem Debuggen einer verwalteten Sprache:  
  
-   Die **"Auto"** Fenster zeigt keine F#-Variablen.  
  
-   Bearbeiten und Fortfahren wird für F# nicht unterstützt. Das Bearbeiten von F#-Code während einer Debugsitzung ist möglich, sollte aber vermieden werden. Da Codeänderungen während der Debugsitzung nicht übernommen werden, verursacht das Bearbeiten von F#-Code während des Debuggens einen Konflikt zwischen dem Quellcode und dem gedebuggten Code.  
  
-   Der Debugger erkennt keine F#-Ausdrücke. Übersetzen Sie den Ausdruck in C#-Syntax, um während des F#-Debuggings einen Ausdruck in ein Debuggerfenster oder Dialogfeld einzugeben. Beachten Sie beim Übersetzen eines F#-Ausdrucks in C#, dass C# == als Vergleichsoperator für Gleichheit und F# ein einzelnes = verwendet.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von verwaltetem Code](../debugger/debugging-managed-code.md)



