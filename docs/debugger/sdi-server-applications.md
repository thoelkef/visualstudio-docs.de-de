---
title: SDI-Serveranwendungen | Microsoft Docs
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 9047c9b39bad5f4f790327b5ee65b4de688db9d8
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/18/2018
---
# <a name="sdi-server-applications"></a>SDI-Serveranwendungen
Wenn Sie eine Server SDI-Anwendung debuggen, müssen Sie angeben `/Embedding` oder `/Automation` in der **Befehlszeilenargumente** Eigenschaft in der *Projekt* Eigenschaftenseiten (Dialogfeld) für C/C++, C#-, oder Visual Basic-Projekte.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
## <a name="finding-the-command-line-arguments-property"></a>Suchen der Eigenschaft Befehlszeilenargumente  
 Für den Zugriff auf die *Projekt* Eigenschaftenseiten (Dialogfeld), mit der rechten Maustaste des Projekts im Projektmappen-Explorer, und wählen Sie dann Eigenschaften aus dem Kontextmenü. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [COM und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von COM-Servern](../debugger/how-to-debug-com-servers.md)