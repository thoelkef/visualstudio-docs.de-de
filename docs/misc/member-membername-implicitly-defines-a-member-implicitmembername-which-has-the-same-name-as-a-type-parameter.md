---
title: "Member &quot;&lt;Membername&gt;&quot; definiert den Member &quot;&lt;Name des impliziten Members&gt;&quot; implizit. Dieser hat den gleichen Namen wie ein Typparameter | Microsoft Docs"
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
  - "BC32070"
  - "vbc32070"
helpviewer_keywords: 
  - "BC32070"
ms.assetid: cc0b3fcf-c141-47e2-9b33-d2b91c8bf2d6
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Member &quot;&lt;Membername&gt;&quot; definiert den Member &quot;&lt;Name des impliziten Members&gt;&quot; implizit. Dieser hat den gleichen Namen wie ein Typparameter
Ein Member einer generischen Klasse generiert einen impliziten Member mit demselben Namen wie ein Typparameter für die Klasse.  
  
 Der [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\-Compiler erstellt implizite Member, die bestimmten von Ihnen deklarierten Programmierelementen entsprechen. In der folgenden Tabelle werden diese impliziten oder auch *synthetischen* Member zusammengefasst.  
  
|Deklariertes Element|Implizit erstellte Member|  
|--------------------------|-------------------------------|  
|Enumeration|`value__`\-Member|  
|Ereignis|`add_<eventname>`\-Prozedur<br /><br /> `remove_<eventname>`\-Prozedur<br /><br /> `<eventname>Event`\-Feld<br /><br /> `<eventname>EventHandler`\-Delegat|  
|Eigenschaft|`get_<propertyname>`\-Prozedur<br /><br /> `set_<propertyname>`\-Prozedur|  
|`My.`\-Auflistungsvariable|`m_<variablename>` `Static`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
|`WithEvents`\-Variable|`_<variablename>`\-Variable<br /><br /> `<variablename>`\-Eigenschaft<br /><br /> `get_<variablename>`\-Prozedur<br /><br /> `set_<variablename>`\-Prozedur|  
  
 Aufgrund möglicher Namenskonflikte sollten Sie es vermeiden, deklarierte Programmierelemente in derselben Form wie diese impliziten Member zu benennen. Sie sollten z. B. Elementnamen vermeiden, die mit `get_` oder `set_` beginnen.  
  
 **Fehler\-ID:** BC32070  
  
### So beheben Sie diesen Fehler  
  
-   Wenn der Name des Typparameters geändert werden kann, ändern Sie diesen, um Konflikte mit den in der obigen Tabelle aufgelisteten Namen zu vermeiden.  
  
-   Wenn der Name des Typparameters beibehalten werden muss, ändern Sie den Namen des Klassenmembers, um Konflikte mit den in der obigen Tabelle aufgelisteten Namen zu vermeiden.  
  
## Siehe auch  
 [Declared Element Names](/dotnet/visual-basic/programming-guide/language-features/declared-elements/declared-element-names)   
 [Generische Typen in Visual Basic](/dotnet/visual-basic/programming-guide/language-features/data-types/generic-types)   
 [Type List](/dotnet/visual-basic/language-reference/statements/type-list)