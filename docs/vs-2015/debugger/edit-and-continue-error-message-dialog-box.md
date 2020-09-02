---
title: Dialog Feld "Fehlermeldung bearbeiten und Fortfahren" | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.SupportedButNotAvailable
- vs.debug.ENC.CannotEditWhileException
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue Error Message dialog box
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5437ef982309ef8595f08283f2685e93d346e764
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "62428278"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Fehlermeldungs-Dialogfeld für "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn Sie in einer Sprache Debuggen, die bearbeiten und Fortfahren unterstützt, aber **Bearbeiten und Fortfahren** ist für den Typ der von Ihnen vorgenommenen Codeänderungen nicht verfügbar. Die Fehlermeldung in dem Feld enthält eine ausführlichere Erklärung. Folgende Gründe zum Anzeigen dieses Dialogfelds sind möglich:  
  
- Sie haben versucht, verwalteten Code zu bearbeiten, während nicht verwaltetes Debuggen aktiviert war. "Bearbeiten und Fortfahren" funktioniert nicht bei Debuggen im gemischten Modus.  
  
- Sie haben versucht, SQL Server-Code zu bearbeiten.  
  
- Sie haben versucht, beim Debuggen eines Dr. Watson-dumpcodes Code zu bearbeiten.  
  
- Sie haben versucht, Code zu bearbeiten, nachdem eine nicht behandelte Ausnahme aufgetreten ist, und die Option "**die aufrufsstapel bei nicht behandelten Ausnahmen**entladen" wurde nicht ausgewählt.  
  
- Sie haben versucht, Code zu bearbeiten, während Sie für eine eingebettete Laufzeitanwendung ein Debuggen durchgeführt haben.  
  
- Sie haben versucht, Code in einem Programm zu bearbeiten, das Sie angefügt haben, statt im Menü **Debuggen** zu beginnen.  
  
- Sie haben versucht, optimierten Code zu bearbeiten.  
  
- Sie haben versucht, verwalteten Code zu bearbeiten, obwohl das Ziel eine 64-Bit-Anwendung ist. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (*Projekt* **Eigenschaften**, Registerkarte **Kompilieren** , **Erweiterte Compilereinstellung** .).  
  
- Sie haben versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert und erneut geladen wurde.  
  
- Sie haben versucht, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.  
  
- Sie haben damit begonnen, eine alte Version der Anwendung zu debuggen (da die neue Version Buildfehler enthält).  
  
- Sie haben versucht, Code während dessen Ausführung zu bearbeiten.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **OK**  
 Schließen Sie das Dialogfeld, und brechen Sie den unmittelbar vorausgegangenen Bearbeitungsversuch ab.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)
