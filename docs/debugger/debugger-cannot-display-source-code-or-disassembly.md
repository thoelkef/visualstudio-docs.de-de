---
title: Debugger kann keinen Quellcode oder Disassembly anzeigen | Microsoft Docs
ms.custom: ''
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
ms.openlocfilehash: 313a0e9e5727d776eaeb13f1c4cef8cf3d8d3bb9
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
ms.locfileid: "31472697"
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