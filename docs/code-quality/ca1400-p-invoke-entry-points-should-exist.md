---
title: "CA1400: F&#252;r P/Invoke m&#252;ssen Einstiegspunkte vorhanden sein | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1400"
  - "PInvokeEntryPointsShouldExist"
helpviewer_keywords: 
  - "PInvokeEntryPointsShouldExist"
  - "CA1400"
ms.assetid: 1d64e470-7b2f-4cca-8fb0-ac92829e6332
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1400: F&#252;r P/Invoke m&#252;ssen Einstiegspunkte vorhanden sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeEntryPointsShouldExist|  
|CheckId|CA1400|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine öffentliche oder geschützte Methode ist mit dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> gekennzeichnet.  Entweder konnte die nicht verwaltete Bibliothek nicht gefunden werden, oder die Methode konnte keiner Funktion in der Bibliothek zugeordnet werden.  Wenn die Regel den Methodennamen nicht in genau der angegebenen Form finden kann, wird nach Schreibweisen im ANSI\- oder Breitzeichenformat gesucht, wobei an den Methodennamen die Zeichen "A" bzw. "W" gehängt werden.  Wird keine Entsprechung gefunden, versucht die Regel, eine Funktion mithilfe des Namensformats \_\_stdcall \(\_MyMethod@12, wobei 12 die Länge der Argumente darstellt\) zu finden.  Wenn keine Entsprechung gefunden wird und der Methodenname mit "\#" beginnt, sucht die Regel nach der Funktion als Ordnungszahlverweis und nicht als Namensverweis.  
  
## Regelbeschreibung  
 Es ist keine Kompilierzeitüberprüfung verfügbar, mit der sichergestellt werden kann, dass sich Methoden, die mit <xref:System.Runtime.InteropServices.DllImportAttribute> markiert sind, in der nicht verwalteten DLL befinden, auf die verwiesen wird.  Wenn es in der Bibliothek keine Funktion mit dem angegebenen Namen gibt oder wenn die Argumente der Methode nicht mit den Funktionsargumenten übereinstimmen, löst die Common Language Runtime eine Ausnahme aus.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, korrigieren Sie die Methode, die über das <xref:System.Runtime.InteropServices.DllImportAttribute>\-Attribut verfügt.  Stellen Sie sicher, dass die nicht verwaltete Bibliothek existiert und sich im gleichen Verzeichnis befindet wie die Assembly, welche die Methode enthält.  Wenn die Bibliothek vorhanden ist und der Verweis darauf einwandfrei ist, überprüfen Sie, ob der Methodenname, der Rückgabetyp und die Argumentsignatur der Bibliothekfunktion entsprechen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, wenn die nicht verwaltete Bibliothek sich im selben Verzeichnis befindet wie die verwaltete Assembly, die auf diese Bibliothek verweist.  Eine Warnung dieser Regel kann u. U. gefahrlos unterdrückt werden, wenn die nicht verwaltete Bibliothek nicht gefunden wurde.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Typ veranschaulicht, der gegen die Regel verstößt.  In kernel32.dll ist keine Funktion mit dem Namen `DoSomethingUnmanaged` vorhanden.  
  
 [!code-cs[FxCop.Interoperability.DLLExists#1](../code-quality/codesnippet/CSharp/ca1400-p-invoke-entry-points-should-exist_1.cs)]  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>