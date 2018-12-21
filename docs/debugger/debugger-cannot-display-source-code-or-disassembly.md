---
title: Debugger kann keinen Quellcode oder Disassembly anzeigen.
ms.custom: seodec18
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- disassembly code, errors
ms.assetid: 112d3ea3-fdd2-4bce-92b4-167a76258934
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ea95a2bb4c29f8a23fd597173a10a838baca051c
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: de-DE
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063965"
---
# <a name="debugger-cannot-display-source-code-or-disassembly"></a>Debugger kann keinen Quellcode oder Disassembly anzeigen
Inhalt dieses Fehlers:  
  
 Der Debugger kann keinen Quellcode oder Disassembly für die aktuelle Position anzeigen.  
  
 Diese Fehlermeldung kann mehrere Ursachen haben:  
  
-   Während des Debuggens einer Sprache, die die Disassembly nicht unterstützt, wurde ein Haltepunkt an einer Position erreicht, für die kein Quellcode vorhanden ist. Öffnen der **Haltepunkte** , suchen Sie den Haltepunkt, und löschen Sie sie.  
  
-   Beim Debuggen von Skripts wurde ein Haltepunkt erreicht, während das Programm keine Threads enthielt. Wählen Sie im Menü **Debuggen** die Option **Schritt** oder **Weiter** aus, um das Debuggen fortzusetzen.  
  
-   Der Debugger konnte aus Sicherheitsgründen keine Stapel-, Register- und andere Kontextinformationen aus dem zu debuggenden Programm lesen. Dies passiert meistens, wenn Sie eine Webanwendung debuggen und nicht die erforderlichen Berechtigungen für den Zugriff auf das virtuelle Verzeichnis haben. Setzen Sie die Berechtigung für das virtuelle Verzeichnis auf Anonym, und führen Sie den Vorgang erneut aus.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen in Visual Studio](../debugger/index.md) [Debugger – Featuretour](../debugger/debugger-feature-tour.md)   
 [Anzeigen von Daten im Debugger](../debugger/viewing-data-in-the-debugger.md)