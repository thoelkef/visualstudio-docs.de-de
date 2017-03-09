---
title: "Die &lt;Klassenname&gt;-Klasse muss als MustInherit deklariert werden oder folgende geerbte MustOverride-Member &#252;berschreiben: &lt;Membername(n)&gt;. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30610"
  - "vbc30610"
helpviewer_keywords: 
  - "BC30610"
ms.assetid: 7fba7a3b-c918-44ba-ae85-20312615c1ce
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die &lt;Klassenname&gt;-Klasse muss als MustInherit deklariert werden oder folgende geerbte MustOverride-Member &#252;berschreiben: &lt;Membername(n)&gt;.
Von Basisklassen abgeleitete Klassen, die `MustOverride`\-Member enthalten, müssen diese Member überschreiben oder den `MustInherit`\-Modifizierer verwenden.  
  
 **Fehler\-ID:** BC30610  
  
### So beheben Sie diesen Fehler  
  
-   Fügen Sie der Klassendefinition den `MustInherit`\-Modifizierer hinzu.  
  
-   Deklarieren Sie mit dem `Overrides`\-Schlüsselwort eine Überschreibung.  
  
## Siehe auch  
 [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)   
 [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)   
 [NICHT IM BUILD: Vererbung in Visual Basic](http://msdn.microsoft.com/de-de/e5e6e240-ed31-4657-820c-079b7c79313c)