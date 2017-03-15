---
title: "&quot;&lt;Basisschnittstellenname&gt;.&lt;Membername&gt;&quot; aus &quot;implements &lt;Name der abgeleiteten Schnittstelle&gt;&quot; wird bereits durch die Basisklasse &quot;&lt;Basisklassenname&gt;&quot; implementiert. Die erneute Implementierung von &lt;Typ&gt; wird angenommen. | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc42014"
  - "vbc42014"
helpviewer_keywords: 
  - "BC42014"
ms.assetid: 95fff622-5d54-4ec8-90f0-477de1d58687
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &quot;&lt;Basisschnittstellenname&gt;.&lt;Membername&gt;&quot; aus &quot;implements &lt;Name der abgeleiteten Schnittstelle&gt;&quot; wird bereits durch die Basisklasse &quot;&lt;Basisklassenname&gt;&quot; implementiert. Die erneute Implementierung von &lt;Typ&gt; wird angenommen.
Eine Eigenschaft, Prozedur oder ein Ereignis in einer abgeleiteten Klasse verwendet eine `Implements`\-Klausel, die einen abgeleiteten Schnittstellenmember angibt, der bereits für die Basisschnittstelle in der Basisklasse implementiert wurde.  
  
 Der zu implementierende Member wird durch die Basisschnittstelle definiert und von der abgeleiteten Schnittstelle geerbt. Die Basisschnittstelle wird direkt von der Basisklasse implementiert. Die abgeleitete Schnittstelle wird durch die abgeleitete Klasse implementiert. Dadurch wird leicht übersehen, dass der Member bereits von der Basisklasse implementiert wurde.  
  
 Ein Schnittstellenmember, der von seiner Basisklasse implementiert wird, kann von einer abgeleiteten Klasse erneut implementiert werden. Dieser Vorgang ist nicht identisch mit dem Überschreiben der Basisklassenimplementierung. Weitere Informationen finden Sie unter [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause).  
  
 Standardmäßig ist diese Meldung eine Warnung. Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC42014  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie beabsichtigen, den Schnittstellenmember erneut zu implementieren, müssen Sie keine Maßnahme ergreifen. Der Code in der abgeleiteten Klasse greift auf den neu implementierten Member zu, sofern nicht das Schlüsselwort [MyBase \- delete](http://msdn.microsoft.com/de-de/52491d06-6451-4f6f-9aa6-8fab59bbc2b9) für den Zugriff auf die Basisklassenimplementierung verwendet wird.  
  
-   Wenn Sie keine erneute Implementierung des Schnittstellenmembers beabsichtigen, entfernen Sie die `Implements`\-Klausel aus der Deklaration der Eigenschaft, Prozedur oder des Ereignisses.  
  
## Siehe auch  
 [Interfaces](/dotnet/visual-basic/programming-guide/language-features/interfaces/index)   
 [NICHT IM BUILD: Implements\-Schlüsselwort und Implements\-Anweisung](http://msdn.microsoft.com/de-de/b96560f7-6413-480f-a1e2-f80253bab5be)