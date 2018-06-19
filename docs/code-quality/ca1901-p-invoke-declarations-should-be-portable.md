---
title: 'CA1901: Deklarationen von P / Invoke müssen portabel sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ed9821d9b80309311a6fd108c4a29f52b2e882bf
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31915020"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklarationen von P/Invoke müssen portabel sein
|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechend – Wenn P/Invoke außerhalb der Assembly sichtbar ist. Nicht unterbrechend – Wenn P/Invoke nicht außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P/Invoke und stellt sicher, dass ihre Größe beim Marshallen an nicht verwalteten Code auf 32-Bit und 64-Bit-Plattformen richtig ist. Die am häufigsten verwendete Verstoß gegen diese Regel ist eine Ganzzahl mit fester Größe übergeben, eine Variable mit plattformabhängige Zeigergröße erforderlich ist.

## <a name="rule-description"></a>Regelbeschreibung
 Die folgenden beiden Szenarien verstößt gegen diese Regel tritt auf:

-   Der Rückgabewert oder Parameter als Ganzzahl fester Größe typisiert ist, wenn er als eingegeben werden, sollte ein `IntPtr`.

-   Der Rückgabewert oder Parameter als typisiert ist, eine `IntPtr` Wenn muss als ganze Zahl fester Größe eingegeben werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sie können diesen Verstoß beheben, indem Sie mithilfe von `IntPtr` oder `UIntPtr` Handles anstelle von darstellen `Int32` oder `UInt32`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Warnung sollte nicht unterdrückt werden.

## <a name="example"></a>Beispiel
 Das folgende Beispiel zeigt einen Verstoß gegen diese Regel.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 In diesem Beispiel wird die `nIconIndex` Parameter deklariert wurde, als ein `IntPtr`, der 4 Bytes, die auf einem 32-Bit-Plattform und 8 Bytes, die auf einer 64-Bit-Plattform breit breit ist. In der folgenden nicht verwalteten Deklaration können Sie sehen, die `nIconIndex` ist auf allen Plattformen eine 4-Byte-Ganzzahl ohne Vorzeichen.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Beispiel
 Um den Verstoß zu beheben, ändern Sie die Deklaration wie folgt aus:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)] 
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Siehe auch
 [Portability Warnings](../code-quality/portability-warnings.md)