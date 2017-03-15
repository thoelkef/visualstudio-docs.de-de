---
title: "CA2121: Statische Konstruktoren sollten privat sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
helpviewer_keywords: 
  - "CA2121"
  - "StaticConstructorsShouldBePrivate"
ms.assetid: ee93c620-8fc1-4e47-866c-d389c3ca9f2e
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2121: Statische Konstruktoren sollten privat sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|StaticConstructorsShouldBePrivate|  
|CheckId|CA2121|  
|Kategorie \(Category\)|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Ein Typ verfügt über einen statischen Konstruktor, der nicht privat ist.  
  
## Regelbeschreibung  
 Statische Konstruktoren, auch als Klassenkonstruktoren bezeichnet, werden verwendet, um einen Typ zu initialisieren.  Das System ruft den statischen Konstruktor auf, bevor die erste Instanz des Typs erzeugt wird bzw. bevor auf irgendwelche statischen Member verwiesen wird.  Der Benutzer hat keine Möglichkeit zu beeinflussen, wann der statische Konstruktor aufgerufen wird.  Wenn ein statischer Konstruktor nicht privat ist, kann er von Code aufgerufen werden, der nicht Systemcode ist.  Je nach den Operationen innerhalb des Konstruktors kann dies zu unerwartetem Verhalten führen.  
  
 Die Durchsetzung dieser Regel wird vom C\#\- und Visual Basic .NET\-Compiler erzwungen.  
  
## Behandeln von Verstößen  
 Verstöße werden i. d. R. von einer der folgenden Aktionen verursacht:  
  
-   Sie haben einen statischen Konstruktor für den Typ definiert, ihn aber nicht als privat definiert.  
  
-   Der Programmiersprachencompiler hat dem Typ einen statischen Standardkonstruktor hinzugefügt, ihn aber nicht als privat definiert.  
  
 Um die erste Art von Verstoß zu korrigieren, definieren Sie den statischen Konstruktor als privat.  Um die zweite Art von Verstoß zu korrigieren, fügen Sie dem Typ einen privaten statischen Konstruktor hinzu.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie diese Verstöße nicht.  Wenn es in Ihrem Softwareentwurf erforderlich ist, dass ein statischer Konstruktor explizit aufgerufen wird, hat der Entwurf wahrscheinlich ernsthafte Fehler und sollte überarbeitet werden.