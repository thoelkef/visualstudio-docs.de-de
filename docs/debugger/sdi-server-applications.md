---
title: SDI-Serveranwendungen | Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: feec570217240c7b7dd7d71b7f40987b756869de
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="sdi-server-applications"></a>SDI-Serveranwendungen
Wenn Sie eine Server SDI-Anwendung debuggen, müssen Sie angeben `/Embedding` oder `/Automation` in der **Befehlszeilenargumente** Eigenschaft in der *Projekt* Eigenschaftenseiten (Dialogfeld) für C/C++, C#-, oder Visual Basic-Projekte.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
## <a name="finding-the-command-line-arguments-property"></a>Suchen der Eigenschaft Befehlszeilenargumente  
 Für den Zugriff auf die *Projekt* Eigenschaftenseiten (Dialogfeld), mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie dann Eigenschaften aus dem Kontextmenü. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [COM und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von COM-Servern](../debugger/how-to-debug-com-servers.md)