---
title: "Member &#39;&lt;Membername1&gt;&#39; deklariert implizit &#39;&lt;Name des impliziten Members&gt;&#39;, was zu einem Konflikt mit einem Member in der Basisklasse &#39;&lt;Basisklassenname&gt;&#39; f&#252;hrt. | Microsoft Docs"
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
  - "vbc40022"
  - "bc40022"
helpviewer_keywords: 
  - "BC40022"
ms.assetid: be5bb2ee-2274-42b2-b843-179b14127b34
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &#39;&lt;Membername1&gt;&#39; deklariert implizit &#39;&lt;Name des impliziten Members&gt;&#39;, was zu einem Konflikt mit einem Member in der Basisklasse &#39;&lt;Basisklassenname&gt;&#39; f&#252;hrt.
Member '\<Membername1\>' deklariert implizit '\<Name des impliziten Members\>', was zu einem Konflikt mit einem Member in der Basisklasse '\<Basisklassenname\>' führt. Daher sollte der Member nicht als 'Overloads' deklariert werden.  
  
 Eine Eigenschaft in einer abgeleiteten Klasse generiert einen impliziten Member mit demselben Namen wie für ein Member der Basisklasse und gibt das [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)\-Schlüsselwort an.  
  
 Überladen wird verwendet, um mehrere Versionen einer Eigenschaft oder Prozedur in derselben Klasse zu definieren. Sie können keine zusätzliche Version eines Basisklassenmembers definieren, es sei denn, der Basisklassenmember gibt bereits `Overloads` an. Da der in Konflikt stehende Basisklassenmember `Overloads` nicht angibt, geht der Compiler davon aus, dass diese Eigenschaft den impliziten Member der Basisklasse überschattet \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\).  
  
 Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler erstellt implizite Member, die bestimmten von Ihnen deklarierten Programmierelementen entsprechen. In der folgenden Tabelle werden diese impliziten oder auch *synthetischen* Member zusammengefasst.  
  
|Deklariertes Element|Implizit erstellte Member|  
|--------------------------|-------------------------------|  
|Enumeration|`value__`\-Member|  
|Ereignis|`add_<eventname>`\-Prozedur<br /><br /> `remove_<eventname>`\-Prozedur<br /><br /> `<eventname>Event`\-Feld<br /><br /> `<eventname>EventHandler`\-Delegat|  
|Eigenschaft|`get_<propertyname>`\-Prozedur<br /><br /> `set_<propertyname>`\-Prozedur|  
|`My.Form`\-Member, `My.WebService`\-Member oder Member einer mit dem Attribut <xref:Microsoft.VisualBasic.MyGroupCollectionAttribute> gekennzeichneten Klasse|`m_<variablename>` `Static`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
|`WithEvents`\-Variable|`_<variablename>`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
  
 Aufgrund des Risikos von Namenskonflikten sollten Sie vermeiden, deklarierte Programmierelemente in derselben Form wie eines dieser impliziten Member zu benennen. Sie sollten z. B. Elementnamen vermeiden, die mit `get_` oder `set_` beginnen.  
  
 Standardmäßig ist diese Meldung eine Warnung. Weitere Informationen zum Ausblenden von Warnungen oder zum Behandeln von Warnungen als Fehler finden Sie unter [Konfigurieren von Warnungen in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **Fehler\-ID:** BC40022  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie den Basisklassenmember ausblenden oder überschatten möchten, sollten Sie das [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)\-Schlüsselwort in die Deklaration der Eigenschaft durch das [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\-Schlüsselwort ersetzen.  
  
-   Wenn Sie nicht beabsichtigen, den Basisklassenmember zu überschatten, ändern Sie den Namen der Eigenschaft, um Konflikte mit den in der obigen Tabelle aufgelisteten Namen zu vermeiden.  
  
## Siehe auch  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)