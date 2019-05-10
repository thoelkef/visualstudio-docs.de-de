---
title: 'Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c57a9ce2b5a1ce9de0ffadb4b623ef3a33b8e9ab
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58956998"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Diese Warnmeldung wird bei Verwendung des Quellservers angezeigt. Diese Meldung besagt, dass der Befehl, den der Debugger zum Abrufen von Quellcode ausführen muss, nicht in der Liste der vertrauenswürdigen Befehle für Quellserver in der Datei "srcsvr.ini" aufgeführt ist. Wenn dies ein gültiger Befehl ist, können Sie ihn der Datei "srcsvr.ini" hinzufügen. Andernfalls sollten Sie ihn nicht ausführen. Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Meldungstext  
 **Der Debugger muss den folgenden nicht vertrauenswürdigen Befehl ausführen, um Quellcode vom Quellserver abzurufen.**  
  
 **Wenn die Debugsymboldatei (\*.pdb) nicht aus einer bekannten und vertrauenswürdigen Quelle stammt, ist dieser Befehl möglicherweise ungültig oder kann nicht sicher ausgeführt werden.**  
  
 **Möchten Sie diesen Befehl ausführen?**  
  
## <a name="uielement-list"></a>UIElement-Liste  
 Textfeld  
 Auszuführender Befehl aus der PDB-Datei.  
  
 Run  
 Lässt die Ausführung des Befehls zu.  
  
 Nicht ausführen  
 Beendet die Ausführung des Befehls und das Herunterladen der Datei vom Quellserver.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symboldateien (PDB) und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debugger Security (Debuggersicherheit)](../debugger/debugger-security.md)   
 [Quellserver](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)
