---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Fügt dem Grafikdiagnose\-*HUD* \(Head\-up\-Display\) eine benutzerdefinierte Meldung hinzu.  
  
## Syntax  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Parameter  
 `szMessage`  
 Die dem HUD hinzuzufügende Meldung.  
  
## Hinweise  
 Das Grafikdiagnose\-HUD wird in der linken oberen Ecke der App angezeigt, die unter der Grafikdiagnose ausgeführt wird.  Es werden Laufzeitinformationen über die App und die Erfassung von Grafikinformationen sowie Meldungen angezeigt, die hinzugefügt werden, indem diese Funktion aufgerufen wird.  
  
 Um dem HUD eine Meldung hinzuzufügen, müssen Sie Grafikinformationen nicht aktiv erfassen – d. h. eine Meldung kann durch eine Instanz der `VsgDbg`\-Klasse hinzugefügt werden, die [Init](../debugger/init.md)\-Memberfunktion muss jedoch nicht zuerst aufgerufen werden.  Meldungen werden nur im HUD angezeigt, sie werden nicht in der Grafikprotokolldatei aufgezeichnet.