---
title: "Eigenschaftenaccessoren k&#246;nnen in einer NotOverridable-Eigenschaft nicht als &quot;&lt;Zugriffsmodifizierer&gt;&quot; deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31106"
  - "bc31106"
helpviewer_keywords: 
  - "BC31106"
ms.assetid: 84bcb157-9c33-4e4f-89a9-c5e6cb73028b
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Eigenschaftenaccessoren k&#246;nnen in einer NotOverridable-Eigenschaft nicht als &quot;&lt;Zugriffsmodifizierer&gt;&quot; deklariert werden.
Eine [Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) oder [Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement) in einer `NotOverridable`\-Eigenschaft enthält das `Private`\-Schlüsselwort.  
  
 Anhand der folgenden logischen Beschreibung wird erläutert, warum `NotOverridable` und `Private` nicht in einer [Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) kombiniert werden können:  
  
1.  Eine Eigenschaft oder Prozedur, die keine Basisklasseneigenschaft bzw. \-prozedur überschreibt, hat die Standardeinstellung [NotOverridable](/dotnet/visual-basic/language-reference/modifiers/notoverridable).  
  
2.  Eine Eigenschaft oder Prozedur in einer abgeleiteten Klasse, die eine Basisklasseneigenschaft bzw. \-prozedur überschreibt, hat dagegen die Standardeinstellung [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable). Um die Hierarchie des Überschreibens zu beenden, können Sie diese als `NotOverridable` deklarieren. Dies ist der einzige Kontext, in dem Sie `NotOverridable` verwenden können. Das heißt, Sie können `NotOverridable` nur in Verbindung mit [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides) verwenden.  
  
3.  Ist eine Eigenschaft oder Prozedur einer Basisklasse als [Private](/dotnet/visual-basic/language-reference/modifiers/private) deklariert ist, kann diese Eigenschaft oder Prozedur nicht von einer abgeleiteten Klasse überschrieben werden, da diese nicht auf die Eigenschaft oder Prozedur zugreifen kann. Daher können Sie `Private` nicht in Verbindung mit `Overridable` verwenden.  
  
4.  Um eine Eigenschaft oder Prozedur zu überschreiben, muss die überschreibende Eigenschaft oder Prozedur nicht nur dieselbe Signatur, sondern auch dieselbe Zugriffsebene haben. Das bedeutet, dass eine überschreibende Eigenschaft oder Prozedur `Private` nicht angeben kann, weil eine überschreibbare Eigenschaft oder Prozedur `Private` nicht angeben kann.  
  
5.  Da Sie `NotOverridable` nur für eine überschreibende Eigenschaft oder Prozedur angeben können, können Sie dieses Schlüsselwort nicht mit `Private` kombinieren.  
  
 Aufgrund derselben Logik können die einzelnen Eigenschaftenprozeduren \(`Get` und `Set`\) einer überschreibenden Eigenschaft nicht `Private` sein.  
  
 **Fehler\-ID:** BC31106  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das `Private`\-Schlüsselwort aus der `Get`\- oder `Set`\-Anweisung, oder entfernen Sie die Schlüsselwörter `Overrides` und `NotOverridable` aus der `Property`\-Anweisung.  
  
## Siehe auch  
 [Eigenschaftenprozeduren](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [Differences Between Shadowing and Overriding](/dotnet/visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)