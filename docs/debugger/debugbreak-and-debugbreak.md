---
title: Debug-und __debugbreak | Microsoft-Dokumentation
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- DebugBreak
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [C++], DebugBreak function
- DebugBreak function
- breakpoints, DebugBreak function
ms.assetid: 9787c795-df94-4f48-bc8d-3bf899b67421
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ce99cd360d75472df6326cfaf6a3f4ddb198b6d2
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/22/2019
ms.locfileid: "72738352"
---
# <a name="debugbreak-and-__debugbreak"></a>DebugBreak und "_debugbreak"
Die Win32-Funktion „DebugBreak“ oder die systeminterne Funktion [__debugbreak](/cpp/intrinsics/debugbreak) kann an einer beliebigen Stelle im Code aufgerufen werden. `DebugBreak` und `__debugbreak` haben dieselben Auswirkungen wie das Festlegen eines Haltepunkts an dieser Stelle.

 Da durch `DebugBreak` eine Systemfunktion aufgerufen wird, müssen Systemdebugsymbole installiert werden, um sicherzustellen, dass nach dem Abbrechen die richtigen Aufruflisteninformationen angezeigt werden. Andernfalls sind die vom Debugger angezeigten Aufruflisteninformationen möglicherweise um einen Rahmen verschoben sind. Wenn Sie `__debugbreak` verwenden, sind keine Symbole erforderlich.

## <a name="see-also"></a>Siehe auch
- [Intrinsische Compilerfunktionen](/cpp/intrinsics/compiler-intrinsics)
- [Debuggersicherheit](../debugger/debugger-security.md)
- [Debuggen von nativem Code](../debugger/debugging-native-code.md)
- [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)