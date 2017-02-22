---
title: "CA5122 P/Invoke-Deklarationen sollten nicht sicherungskritisch sein | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 4
caps.handback.revision: 4
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA5122 P/Invoke-Deklarationen sollten nicht sicherungskritisch sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|  
|CheckId|CA5122|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine P\/Invoke\-Deklaration wurde mit <xref:System.Security.SecuritySafeCriticalAttribute> markiert:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers]  
  
// ...  
public class C  
{  
    [SecuritySafeCritical]  
    [DllImport("kernel32.dll")]  
    public static extern bool Beep(int frequency, int duration); // CA5122 – safe critical p/invoke  
   }  
  
```  
  
 In diesem Beispiel wurde `C.Beep(...)` als sicherungskritische Methode markiert.  
  
## Regelbeschreibung  
 Methoden werden als SecuritySafeCritical markiert, wenn sie einen sicherheitsrelevanten Vorgang ausführen. Sie können jedoch auch mit transparentem Code verwendet werden.  Eine der grundlegenden Regeln des Sicherheitstransparenzmodells lautet: Transparenter Code darf systemeigenen Code nie direkt mit P\/Invoke aufrufen.  Wenn daher P\/Invoke als sicherungskritisch markiert wird, kann es nicht von transparentem Code aufgerufen werden, was bei der Sicherheitsanalyse irreführend ist.  
  
## Behandeln von Verstößen  
 Um P\/Invoke für transparenten Code verfügbar zu machen, muss eine sicherungskritische Wrappermethode dafür ausgeführt werden:  
  
```c#  
[assembly: AllowPartiallyTrustedCallers  
  
class C  
{  
   [SecurityCritical]  
   [DllImport(“kernel32.dll”, EntryPoint=”Beep”)]  
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke  
  
   [SecuritySafeCritical]  
   public static bool Beep(int frequency, int duration)  
   {  
      return BeepPInvoke(frequency, duration);  
   }  
}  
  
```  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.