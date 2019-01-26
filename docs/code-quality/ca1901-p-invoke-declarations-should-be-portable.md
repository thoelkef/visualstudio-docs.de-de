---
title: 'CA1901: Deklarationen von P/Invoke müssen portabel sein.'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e74c798cc273fe331118139df99ec890cdcd3086
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2019
ms.locfileid: "55001669"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklarationen von P/Invoke müssen portabel sein.

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategorie|Microsoft.Portability|
|Unterbrechende Änderung|Unterbrechend – Wenn der P/Invoke außerhalb der Assembly sichtbar ist. Nicht unterbrechend – Wenn der P/Invoke nicht außerhalb der Assembly sichtbar ist.|

## <a name="cause"></a>Ursache
 Diese Regel wertet die Größe der einzelnen Parameter und der Rückgabewert einer P/Invoke und stellt sicher, dass ihre Größe, die beim Marshallen an nicht verwalteten Code auf 32-Bit- und 64-Bit-Plattformen richtig ist. Die am häufigsten verwendete Verstoß gegen diese Regel ist eine Ganzzahl mit fester Größe übergeben, eine plattformabhängige, Zeigergröße-Variable, die erforderlich ist.

## <a name="rule-description"></a>Regelbeschreibung
 Eines der folgenden Szenarien verstößt gegen diese Regel auftritt:

- Der Rückgabewert oder Parameter als eine Ganzzahl mit fester Größe typisiert ist, wenn er als eingegeben werden, sollten eine `IntPtr`.

- Der Rückgabewert oder Parameter als typisiert ist ein `IntPtr` Wenn typisiert als eine Ganzzahl mit fester Größe.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sie können diese Verletzung beheben, indem Sie mithilfe von `IntPtr` oder `UIntPtr` Handles anstelle von darstellen `Int32` oder `UInt32`.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken
 Sie sollten nicht auf diese Warnung unterdrücken.

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

 In diesem Beispiel die `nIconIndex` Parameter deklariert wurde, als ein `IntPtr`, der 4 Bytes, die auf einer 32-Bit-Plattform und auf einer 64-Bit-Plattform Breite von 8 Bytes breit ist. In der folgenden nicht verwalteten Deklaration können Sie sehen, die `nIconIndex` auf allen Plattformen eine 4-Byte-Ganzzahl ohne Vorzeichen ist.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Beispiel
 Um die Verletzung zu beheben, ändern Sie die Deklaration wie folgt aus:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Siehe auch
 [Portability Warnings](../code-quality/portability-warnings.md)