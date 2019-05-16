---
title: DebugBreak und __debugbreak | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2a40943233e7dfffd3340f2e27da1d43a76a0a
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/15/2019
ms.locfileid: "65691174"
---
# <a name="debugbreak-and-debugbreak"></a>DebugBreak und "_debugbreak"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die Win32-Funktion „DebugBreak“ oder die systeminterne Funktion [__debugbreak](https://msdn.microsoft.com/library/1d1e1c0c-891a-4613-ae4b-d790094ba830) kann an einer beliebigen Stelle im Code aufgerufen werden. `DebugBreak` und `__debugbreak` haben dieselben Auswirkungen wie das Festlegen eines Haltepunkts an dieser Stelle.  
  
 Da durch `DebugBreak` eine Systemfunktion aufgerufen wird, müssen Systemdebugsymbole installiert werden, um sicherzustellen, dass nach dem Abbrechen die richtigen Aufruflisteninformationen angezeigt werden. Andernfalls sind die vom Debugger angezeigten Aufruflisteninformationen möglicherweise um einen Rahmen verschoben sind. Wenn Sie `__debugbreak` verwenden, sind keine Symbole erforderlich.  
  
## <a name="see-also"></a>Siehe auch  
 [Intrinsische Compilerfunktionen](https://msdn.microsoft.com/library/48bb9929-7d78-4fd8-a092-ae3c9f971858)   
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Debuggen von nativem Code](../debugger/debugging-native-code.md)   
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)
