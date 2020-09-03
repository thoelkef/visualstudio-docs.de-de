---
title: 'Vorgehensweise: Untersuchen von System Code nach einer Ausnahme | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging, exceptions
- exceptions, debugging
ms.assetid: a38ad49b-7cf3-483d-91c4-eb3116eba50c
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c34b2fdf2b6400ffe88f9e9ff08cbe6e4b41daa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155581"
---
# <a name="how-to-examine-system-code-after-an-exception"></a>Vorgehensweise: Untersuchen von Systemcode nach einer Ausnahme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn eine Ausnahme auftritt, müssen Sie unter Umständen Code in einem Systemaufruf prüfen, um die Ursache für die Ausnahme zu ermitteln. Im folgenden Verfahren wird die entsprechende Vorgehensweise erläutert, wenn Sie keine Symbole für den Systemcode geladen haben oder wenn Nur mein Code aktiviert ist.  
  
### <a name="to-examine-system-code-following-an-exception"></a>So prüfen Sie Systemcode nach einer Ausnahme  
  
1. Klicken Sie mit der rechten Maustaste in das Fenster **Aufrufliste**, und klicken Sie dann auf **Externen Code anzeigen**.  
  
     Wenn Nur mein Code nicht aktiviert ist, ist diese Option nicht im Kontextmenü verfügbar, und Systemcode wird standardmäßig angezeigt.  
  
2. Klicken Sie mit der rechten Maustaste auf die externen Codeframes, die jetzt im Fenster **Aufrufliste** angezeigt werden.  
  
3. Zeigen Sie auf **Symbole laden aus**, und klicken Sie dann auf **Microsoft-Symbolserver**.  
  
    1. Wenn Nur mein Code aktiviert wurde, wird ein Dialogfeld angezeigt. Es gibt an, dass Nur mein Code jetzt deaktiviert wurde. Dies ist für die schrittweise Ausführung von Systemaufrufen erforderlich.  
  
    2. Das Dialogfeld **Öffentliche Symbole werden heruntergeladen** wird angezeigt. Nach Abschluss des Downloadvorgangs wird das Dialogfeld geschlossen.  
  
4. Sie können jetzt den Systemcode im Fenster **Aufrufliste** und anderen Fenstern prüfen. Sie können beispielsweise auf einen Aufruflistenrahmen doppelklicken, um den Code in einer Quelle oder im Fenster **Disassembly** anzuzeigen.  
  
## <a name="see-also"></a>Weitere Informationen  
 [Verwalten von Ausnahmen mit dem Debugger](../debugger/managing-exceptions-with-the-debugger.md)
