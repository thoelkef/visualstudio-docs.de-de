---
title: Bearbeiten und Fortfahren Fehlermeldungsdialogfeld | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.ENC.SupportedButNotAvaiable
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b6252fbaf67a9a5b4173c0fee3f65607e9cc462
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49227232"
---
# <a name="edit-and-continue-error-message-dialog-box"></a>Fehlermeldungs-Dialogfeld für "Bearbeiten und Fortfahren"
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Dieses Dialogfeld wird angezeigt, wenn Sie in einer Programmiersprache Debuggen, das Bearbeiten und fortfahren, unterstützt aber **bearbeiten und Fortfahren** ist für den Typ des von Ihnen vorgenommenen codeänderungen nicht verfügbar. Die Fehlermeldung in dem Feld enthält eine ausführlichere Erklärung. Folgende Gründe zum Anzeigen dieses Dialogfelds sind möglich:  
  
-   Sie haben versucht, verwalteten Code zu bearbeiten, während nicht verwaltetes Debuggen aktiviert war. "Bearbeiten und Fortfahren" funktioniert nicht bei Debuggen im gemischten Modus.  
  
-   Sie haben versucht, SQL Server-Code zu bearbeiten.  
  
-   Sie haben versucht, Code während des Debuggens eines Dr zu bearbeiten. Dr.Watson-Dumps.  
  
-   Sie haben versucht, das Bearbeiten von Code nach dem eine nicht behandelte Ausnahme aufgetreten ist und die Option "**Aufrufliste für Ausnahmefehler entladen**" wurde nicht ausgewählt.  
  
-   Sie haben versucht, Code zu bearbeiten, während Sie für eine eingebettete Laufzeitanwendung ein Debuggen durchgeführt haben.  
  
-   Sie haben versucht, Code in einem Programm, das Sie angefügt und nicht über die **Debuggen** Menü.  
  
-   Sie haben versucht, optimierten Code zu bearbeiten.  
  
-   Sie haben versucht, verwalteten Code zu bearbeiten, obwohl das Ziel eine 64-Bit-Anwendung ist. Wenn Sie Bearbeiten und Fortfahren verwenden möchten, müssen Sie das Ziel auf x86 festlegen. (*Projekt* **Eigenschaften**, **Kompilieren** Registerkarte **erweiterte Compilereinstellungen** festlegen.).  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die während des Debuggens geändert und erneut geladen wurde.  
  
-   Sie haben versucht, Code in einer Assembly zu bearbeiten, die nicht geladen wurde.  
  
-   Sie haben damit begonnen, eine alte Version der Anwendung zu debuggen (da die neue Version Buildfehler enthält).  
  
-   Sie haben versucht, Code während dessen Ausführung zu bearbeiten.  
  
## <a name="uielement-list"></a>UIElement-Liste  
 **OK**  
 Schließen Sie das Dialogfeld, und brechen Sie den unmittelbar vorausgegangenen Bearbeitungsversuch ab.  
  
## <a name="see-also"></a>Siehe auch  
 [Unterstützte Codeänderungen (C++)](../debugger/supported-code-changes-cpp.md)



