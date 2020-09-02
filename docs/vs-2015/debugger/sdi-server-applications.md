---
title: SDI-Server Anwendungen | Microsoft-Dokumentation
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "68148149"
---
# <a name="sdi-server-applications"></a>SDI-Serveranwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Beim Debuggen einer SDI-Serveranwendung müssen Sie für Projekte in C/C++, C# oder Visual Basic im Dialogfeld mit den Eigenschaftenseiten zum *Projekt* in der Eigenschaft **Befehlszeilenargumente** die Option `/Embedding` oder `/Automation` festlegen.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
## <a name="finding-the-command-line-arguments-property"></a>Suchen der Eigenschaft Befehlszeilenargumente  
 Zum Öffnen des Dialogfelds mit den Eigenschaftenseiten zum *Projekt* klicken Sie im Projektmappen-Explorer mit der rechten Maustaste auf das Projekt und klicken anschließend im Kontextmenü auf „Eigenschaften“. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Weitere Informationen  
 [COM-und ActiveX-Debugging](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von COM-Servern](../debugger/how-to-debug-com-servers.md)
