---
title: Debugger kann keinen Quellcode oder Disassembly anzeigen | Microsoft Docs
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
helpviewer_keywords: disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: "7"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 8795ee33a5fc96c979cb67636d3ce5dd23c1b665
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debugger kann keinen Quellcode oder Disassembly anzeigen
Inhalt dieses Fehlers:  
  
 Der Debugger kann keinen Quellcode oder Disassembly für die aktuelle Position anzeigen.  
  
 Diese Fehlermeldung kann mehrere Ursachen haben:  
  
-   Während des Debuggens einer Sprache, die die Disassembly nicht unterstützt, wurde ein Haltepunkt an einer Position erreicht, für die kein Quellcode vorhanden ist. Öffnen der **Haltepunkte** , suchen Sie den Haltepunkt, und löschen Sie ihn.  
  
-   Beim Debuggen von Skripts wurde ein Haltepunkt erreicht, während das Programm keine Threads enthielt. Wählen Sie **Schritt** oder **Fortfahren** aus der **Debuggen** Menü, um das Debuggen fortzusetzen.  
  
-   Der Debugger konnte aus Sicherheitsgründen keine Stapel-, Register- und andere Kontextinformationen aus dem zu debuggenden Programm lesen. Dies passiert meistens, wenn Sie eine Webanwendung debuggen und nicht die erforderlichen Berechtigungen für den Zugriff auf das virtuelle Verzeichnis haben. Setzen Sie die Berechtigung für das virtuelle Verzeichnis auf Anonym, und führen Sie den Vorgang erneut aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md) [Debugger-Funktion Tour](../debugger/debugger-feature-tour.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)