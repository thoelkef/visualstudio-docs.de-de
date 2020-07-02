---
title: CA5122 P-Deklarationen sollten nicht sicher kritisch sein | Microsoft-Dokumentation
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a6a6ee7796ae437b564f6826376219291143e449
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545092"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke-Deklarationen sollten nicht sicherungskritisch sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|PInvokesShouldNotBeSafeCriticalFxCopRule|
|CheckId|CA5122|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine P/Invoke-Deklaration wurde mit <xref:System.Security.SecuritySafeCriticalAttribute> markiert:

```csharp
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

## <a name="rule-description"></a>Beschreibung der Regel
 Methoden werden als SecuritySafeCritical markiert, wenn sie einen sicherheitsrelevanten Vorgang ausführen. Sie können jedoch auch mit transparentem Code verwendet werden. Eine der grundlegenden Regeln des Sicherheitstransparenzmodells lautet: Transparenter Code darf nativen Code nie direkt mit P/Invoke aufrufen. Wenn daher P/Invoke als sicherungskritisch markiert wird, kann es nicht von transparentem Code aufgerufen werden, was bei der Sicherheitsanalyse irreführend ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um P/Invoke für transparenten Code verfügbar zu machen, muss eine sicherungskritische Wrappermethode dafür ausgeführt werden:

```csharp
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

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.
