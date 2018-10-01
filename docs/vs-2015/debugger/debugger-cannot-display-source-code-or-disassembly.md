---
title: Debugger kann keinen Quellcode oder Disassembly anzeigen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 2018-06-30
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
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bd21a38123894e7254bf4af6629528f8af4bf52d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520362"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debugger kann keinen Quellcode oder Disassembly anzeigen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [Debugger kann nicht anzeigen, Quellcode oder Disassembly](https://docs.microsoft.com/visualstudio/debugger/debugger-cannot-display-source-code-or-disassembly).  
  
Inhalt dieses Fehlers:  
  
 Der Debugger kann keinen Quellcode oder Disassembly für die aktuelle Position anzeigen.  
  
 Diese Fehlermeldung kann mehrere Ursachen haben:  
  
-   Während des Debuggens einer Sprache, die die Disassembly nicht unterstützt, wurde ein Haltepunkt an einer Position erreicht, für die kein Quellcode vorhanden ist. Öffnen der **Haltepunkte** , suchen Sie den Haltepunkt, und löschen Sie sie.  
  
-   Beim Debuggen von Skripts wurde ein Haltepunkt erreicht, während das Programm keine Threads enthielt. Wählen Sie **Schritt** oder **Weiter** aus der **Debuggen** Menü, um das Debuggen fortzusetzen.  
  
-   Der Debugger konnte aus Sicherheitsgründen keine Stapel-, Register- und andere Kontextinformationen aus dem zu debuggenden Programm lesen. Dies passiert meistens, wenn Sie eine Webanwendung debuggen und nicht die erforderlichen Berechtigungen für den Zugriff auf das virtuelle Verzeichnis haben. Setzen Sie die Berechtigung für das virtuelle Verzeichnis auf Anonym, und führen Sie den Vorgang erneut aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debugger – Grundlagen](../debugger/debugger-basics.md)   
 [Debuggen in Visual Studio](../debugger/debugging-in-visual-studio.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)



