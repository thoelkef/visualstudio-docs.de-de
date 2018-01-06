---
title: 'Vorgehensweise: Untersuchen von Systemcode nach einer Ausnahme | Microsoft Docs'
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
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: "13"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 2a24b96672c7677943fa7dfe7807c578bf4d64ce
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Gewusst wie: Untersuchen von Systemcode nach einer Ausnahme
Wenn eine Ausnahme auftritt, müssen Sie unter Umständen Code in einem Systemaufruf prüfen, um die Ursache für die Ausnahme zu ermitteln. Im folgenden Verfahren wird die entsprechende Vorgehensweise erläutert, wenn Sie keine Symbole für den Systemcode geladen haben oder wenn Nur mein Code aktiviert ist.  
  
### <a name="to-examine-system-code-following-an-exception"></a>So prüfen Sie Systemcode nach einer Ausnahme  
  
1.  In der **Aufrufliste** Fenster, mit der rechten Maustaste, klicken Sie dann klicken Sie auf **externen Code anzeigen**.  
  
     Wenn Nur mein Code nicht aktiviert ist, ist diese Option nicht im Kontextmenü verfügbar, und Systemcode wird standardmäßig angezeigt.  
  
2.  Mit der rechten Maustaste die externen Codeframes, die jetzt in angezeigt werden, der die **Aufrufliste** Fenster.  
  
3.  Zeigen Sie auf **Symbole laden aus** , und klicken Sie dann auf **Microsoft-Symbolserver**.  
  
    1.  Wenn Nur mein Code aktiviert wurde, wird ein Dialogfeld angezeigt. Es gibt an, dass Nur mein Code jetzt deaktiviert wurde. Dies ist für die schrittweise Ausführung von Systemaufrufen erforderlich.  
  
    2.  Die **öffentliche Symbole werden heruntergeladen** Dialogfeld wird angezeigt. Nach Abschluss des Downloadvorgangs wird das Dialogfeld geschlossen.  
  
4.  Sie können jetzt den Systemcode im Untersuchen der **Aufrufliste** Fenster und anderen Fenstern. Sie können z. B. einen Aufruflistenrahmen zum Anzeigen des Codes in einer Datenquelle doppelklicken oder **Disassembly** Fenster.  
  
## <a name="see-also"></a>Siehe auch  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)