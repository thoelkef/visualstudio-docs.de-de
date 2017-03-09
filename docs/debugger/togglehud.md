---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Schaltet die *HUD*\-Überlagerung \(Head\-Up\-Display\) der Grafikdiagnose ein oder aus.  
  
## Syntax  
  
```cpp  
void ToggleHUD();  
```  
  
## Hinweise  
 Das Grafikdiagnose\-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird.  Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die durch Aufrufen der [AddMessage](../debugger/addmessage.md)\-Memberfunktion hinzugefügt werden.  
  
 Um das HUD ein\- und auszuschalten, müssen Sie Grafikinformationen nicht aktiv aufzeichnen – d. h. es kann durch eine Instanz der `VsgDbg`\-Klasse ein\- und ausgeschaltet werden, aber die Memberfunktion [Init](../debugger/init.md) muss nicht zuerst aufgerufen werden.