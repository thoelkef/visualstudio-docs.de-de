---
title: CA5122 P-Invoke-Deklarationen sollten nicht sicherungskritisch sein
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: f2581a6d-2a0e-40c1-b600-f5dc70909200
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9abe71337b5eb09d44ec6a244dc17e656768847a
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/08/2019
ms.locfileid: "55907879"
---
# <a name="ca5122-pinvoke-declarations-should-not-be-safe-critical"></a>CA5122 P/Invoke-Deklarationen sollten nicht sicherungskritisch sein

|||
|-|-|
|TypeName|PInvokesShouldNotBeSafeCriticalFxCopRule|
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
    public static extern bool Beep(int frequency, int duration); // CA5122 - safe critical p/invoke
   }
```

 In diesem Beispiel wurde `C.Beep(...)` als sicherungskritische Methode markiert.

## <a name="rule-description"></a>Regelbeschreibung
 Methoden werden als SecuritySafeCritical markiert, wenn sie einen sicherheitsrelevanten Vorgang ausführen. Sie können jedoch auch mit transparentem Code verwendet werden. Eine der grundlegenden Regeln des Sicherheitstransparenzmodells lautet: Transparenter Code darf systemeigenen Code nie direkt mit P/Invoke aufrufen. Wenn daher P/Invoke als sicherungskritisch markiert wird, kann es nicht von transparentem Code aufgerufen werden, was bei der Sicherheitsanalyse irreführend ist.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um P/Invoke für transparenten Code verfügbar zu machen, muss eine sicherungskritische Wrappermethode dafür ausgeführt werden:

```csharp
[assembly: AllowPartiallyTrustedCallers

class C
{
   [SecurityCritical]
   [DllImport("kernel32.dll", EntryPoint="Beep")]
   private static extern bool BeepPinvoke(int frequency, int duration); // Security Critical P/Invoke

   [SecuritySafeCritical]
   public static bool Beep(int frequency, int duration)
   {
      return BeepPInvoke(frequency, duration);
   }
}
```

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Unterdrücken Sie keine Warnung dieser Regel.