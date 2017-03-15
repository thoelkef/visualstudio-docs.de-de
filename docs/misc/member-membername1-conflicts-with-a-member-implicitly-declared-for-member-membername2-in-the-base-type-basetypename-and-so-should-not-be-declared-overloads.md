---
title: "Member &lt;Membername1&gt; steht mit einem Member in Konflikt, der implizit f&#252;r den Member &lt;Membername2&gt; im Basistyp &lt;Basistypname&gt; deklariert wurde, und sollte daher nicht als „Overloads“ deklariert werden. | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc40023"
  - "bc40023"
helpviewer_keywords: 
  - "BC40023"
ms.assetid: 82bb29a6-8d49-47a4-8c19-b21e97dfc7de
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &lt;Membername1&gt; steht mit einem Member in Konflikt, der implizit f&#252;r den Member &lt;Membername2&gt; im Basistyp &lt;Basistypname&gt; deklariert wurde, und sollte daher nicht als „Overloads“ deklariert werden.
Eine Eigenschaft oder Prozedur in einer abgeleiteten Klasse verwendet den gleichen Namen wie ein impliziter Member der Basisklasse und gibt das [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)\-Schlüsselwort an.  
  
 Überladen wird verwendet, um mehrere Versionen einer Eigenschaft oder Prozedur in derselben Klasse zu definieren. Sie können keine zusätzliche Version eines Basisklassenmembers definieren, es sei denn, der Basisklassenmember gibt bereits `Overloads` an. Da implizite Member `Overloads` nicht angeben, geht der Compiler davon aus, dass diese Eigenschaft oder Prozedur den impliziten Member der Basisklasse überschattet \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\).  
  
 Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler erstellt implizite Member, die bestimmten von Ihnen deklarierten Programmierelementen entsprechen. In der folgenden Tabelle werden diese impliziten oder auch *synthetischen* Member zusammengefasst.  
  
|Deklariertes Element|Implizit erstellte Member|  
|--------------------------|-------------------------------|  
|Enumeration|`value__`\-Member|  
|Ereignis|`add_<eventname>`\-Prozedur<br /><br /> `remove_<eventname>`\-Prozedur<br /><br /> `<eventname>Event`\-Feld<br /><br /> `<eventname>EventHandler`\-Delegat|  
|Eigenschaft|`get_<propertyname>`\-Prozedur<br /><br /> `set_<propertyname>`\-Prozedur|  
|`My.Form`\-Member, `My.WebService`\-Member oder Member einer mit dem Attribut <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> gekennzeichneten Klasse|`m_<variablename>` `Static`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
|`WithEvents`\-Variable|`_<variablename>`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
  
 Aufgrund des Risikos von Namenskonflikten sollten Sie vermeiden, deklarierte Programmierelemente in derselben Form wie eines dieser impliziten Member zu benennen. Sie sollten z. B. Elementnamen vermeiden, die mit `get_` oder `set_` beginnen.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen und zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40023  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie den Namen der Eigenschaft oder Prozedur, um Konflikte mit den in der oben stehenden Tabelle aufgelisteten Namen zu vermeiden.  
  
## Siehe auch  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)