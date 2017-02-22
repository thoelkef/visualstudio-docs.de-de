---
title: "CA1822: Member als statisch markieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkMembersAsStatic"
  - "CA1822"
helpviewer_keywords: 
  - "MarkMethodsAsStatic"
  - "CA1822"
ms.assetid: 743f0af7-41d1-4852-8d97-af0688b31118
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1822: Member als statisch markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkMembersAsStatic|  
|CheckId|CA1822|  
|Kategorie \(Category\)|Microsoft.Performance|  
|Unterbrechende Änderung|Nicht unterbrechend – Wenn der Member unabhängig von der vorgenommenen Änderung außerhalb der Assembly nicht sichtbar ist.  Nicht unterbrechend – Wenn Sie nur den Member mit dem `this`\-Schlüsselwort in einen Instanzmember ändern.<br /><br /> Unterbrechend – Wenn Sie den Member von einem Instanzmember in einen statischen Member ändern und er außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Ein Member, der nicht auf Instanzdaten zugreift, ist nicht als statisch markiert \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  
  
## Regelbeschreibung  
 Member, die nicht auf Instanzdaten zugreifen oder keine Instanzmethoden aufrufen, können als static markiert werden \(Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\).  Danach gibt der Compiler nicht virtuelle Aufrufsites an diese Member aus.  wodurch eine Überprüfung zur Laufzeit aller Aufrufe verhindert wird, die sicherstellt, dass der aktuelle Objektzeiger ungleich NULL ist.  Dies kann zu einer messbaren Leistungssteigerung für leistungsabhängigen Code führen.  In manchen Fällen stellt es ein Problem mit der Richtigkeit dar, wenn nicht auf die aktuelle Objektinstanz zugegriffen werden kann.  
  
## Behandeln von Verstößen  
 Markieren Sie den Member als statisch \(oder Shared in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\), oder verwenden Sie im Methodentext ggf. 'this'\/'Me'.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann bei zuvor veröffentlichtem Code, für den die Korrektur eine unterbrechende Änderung wäre, gefahrlos unterdrückt werden.  
  
## Verwandte Regeln  
 [CA1811: Nicht aufgerufenen privaten Code vermeiden](../code-quality/ca1811-avoid-uncalled-private-code.md)  
  
 [CA1812: Nicht instanziierte interne Klassen vermeiden](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)  
  
 [CA1804: Nicht verwendete lokale Variablen entfernen](../code-quality/ca1804-remove-unused-locals.md)