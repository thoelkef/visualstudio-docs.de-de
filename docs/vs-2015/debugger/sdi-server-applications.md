---
title: SDI-Serveranwendungen | Microsoft-Dokumentation
ms.custom: ''
ms.date: 11/15/2016
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
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba975d21e1fbef2d32b45dd4ebdc758e8b6cf575
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49199068"
---
# <a name="sdi-server-applications"></a>SDI-Serveranwendungen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Wenn Sie eine SDI-Serveranwendung Debuggen, müssen Sie angeben `/Embedding` oder `/Automation` in die **Befehlszeilenargumente** -Eigenschaft in der *Projekt* Eigenschaftenseiten-Dialogfeld für C/C++, c# oder Visual Basic-Projekte.  
  
 Mithilfe dieser Befehlszeilenargumente kann die Serveranwendung vom Debugger wie von einem Container aus gestartet werden. Das Starten des Containers im Programm-Manager oder Datei-Manager bewirkt dann, dass der Container die im Debugger gestartete Instanz des Servers verwendet.  
  
## <a name="finding-the-command-line-arguments-property"></a>Suchen der Eigenschaft Befehlszeilenargumente  
 Für den Zugriff auf die *Projekt* im Dialogfeld Eigenschaftenseiten, mit der rechten Maustaste in des Projekts im Projektmappen-Explorer, und wählen Sie dann Eigenschaften aus dem Kontextmenü. Die Eigenschaft Befehlszeilenargumente wird angezeigt, wenn Sie die Kategorie Konfigurationseigenschaften erweitern und dann auf die Seite Debuggen klicken.  
  
## <a name="see-also"></a>Siehe auch  
 [Debuggen von COM und ActiveX](../debugger/com-and-activex-debugging.md)   
 [Gewusst wie: Debuggen von COM-Servern](../debugger/how-to-debug-com-servers.md)



