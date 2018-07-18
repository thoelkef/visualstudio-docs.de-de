---
title: 'Sicherheitshinweis: Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.sourceserver.securityalert
dev_langs:
- CSharp
- VB
- FSharp
- C++
ms.assetid: e5c004b3-b364-4098-ac98-770076ca9981
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 77554795772a5a9e2ce5d9bbe9f620923bc20184
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31479928"
---
# <a name="security-warning-debugger-must-execute-untrusted-command"></a>Sicherheitswarnung: Der Debugger muss diesen nicht vertrauenswürdigen Befehl ausführen
Diese Warnmeldung wird bei Verwendung des Quellservers angezeigt. Diese Meldung besagt, dass der Befehl, den der Debugger zum Abrufen von Quellcode ausführen muss, nicht in der Liste der vertrauenswürdigen Befehle für Quellserver in der Datei "srcsvr.ini" aufgeführt ist. Wenn dies ein gültiger Befehl ist, können Sie ihn der Datei "srcsvr.ini" hinzufügen. Andernfalls sollten Sie ihn nicht ausführen. Weitere Informationen finden Sie unter [Angeben von Symbol (.pdb)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
## <a name="message-text"></a>Meldungstext  
 **Der Debugger muss die folgenden nicht vertrauenswürdigen Befehl zum Abrufen von Quellcode vom Quellserver ausführen.**  
  
 **Wenn das Debuggen Datei symbol (\*PDB-Datei) wird nicht von einer bekannten und vertrauenswürdigen Quelle dieser Befehl möglicherweise ungültig oder kann zum Ausführen.**  
  
 **Möchten Sie diesen Befehl ausführen?**  
  
## <a name="uielement-list"></a>UIElement-Liste  
 Textfeld  
 Auszuführender Befehl aus der PDB-Datei.  
  
 Run  
 Lässt die Ausführung des Befehls zu.  
  
 Nicht ausführen  
 Beendet die Ausführung des Befehls und das Herunterladen der Datei vom Quellserver.  
  
## <a name="see-also"></a>Siehe auch  
 [Angeben von Symbol(PDB)- und Quelldateien](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Debuggersicherheit](../debugger/debugger-security.md)   
 [Quellserver](http://msdn.microsoft.com/library/windows/desktop/ms680641\(v=vs.85\).aspx)