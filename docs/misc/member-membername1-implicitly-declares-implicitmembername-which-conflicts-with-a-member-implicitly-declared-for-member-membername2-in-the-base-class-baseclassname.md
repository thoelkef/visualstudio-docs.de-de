---
title: "Member &quot;&lt;Membername1&gt;&quot; deklariert implizit &quot;&lt;Name des impliziten Members&gt;, was zu einem Konflikt mit einem Member f&#252;hrt, der implizit f&#252;r Member &quot;&lt;Membername2&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; deklariert wird. | Microsoft Docs"
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
  - "vbc40018"
  - "bc40018"
helpviewer_keywords: 
  - "BC40018"
ms.assetid: 43844e55-9ce1-4b88-9aa8-839b37f30e5a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &quot;&lt;Membername1&gt;&quot; deklariert implizit &quot;&lt;Name des impliziten Members&gt;, was zu einem Konflikt mit einem Member f&#252;hrt, der implizit f&#252;r Member &quot;&lt;Membername2&gt;&quot; in der Basisklasse &quot;&lt;Basisklassenname&gt;&quot; deklariert wird.
Member "\<Membername1\>" deklariert implizit "\<Name des impliziten Members\>, was zu einem Konflikt mit einem Member führt, der implizit für Member "\<Membername2\>" in der Basisklasse "\<Basisklassenname\>" deklariert wird. Daher sollte der Member als "Shadows" deklariert werden.  
  
 Ein Member einer abgeleiteten Klasse generiert einen impliziten Member mit demselben Namen wie ein impliziter Member der Basisklasse. Da implizite Member [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) nicht angeben, geht der Compiler davon aus, dass dieser Member den impliziten Member der Basisklasse überschattet \([Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\). Der Code ist besser lesbar und weniger fehleranfällig, wenn Sie das `Shadows`\-Schlüsselwort für diesen Member explizit angeben.  
  
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
  
 **Fehler\-ID:** BC40018  
  
### So beheben Sie diesen Fehler  
  
-   Wenn Sie den impliziten Member der Basisklasse ausblenden oder überschatten möchten, sollten Sie das [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)\-Schlüsselwort in die Deklaration des Members der abgeleiteten Klasse aufnehmen.  
  
-   Wenn Sie nicht beabsichtigen, den impliziten Member der Basisklasse zu überschatten, ändern Sie den Namen des Members der abgeleiteten Klasse, um Konflikte mit den in der obigen Tabelle aufgelisteten Namen zu vermeiden.  
  
## Siehe auch  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)