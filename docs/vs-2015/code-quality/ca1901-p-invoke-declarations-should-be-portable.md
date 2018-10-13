---
title: 'CA1901: Deklarationen von P / Invoke müssen portabel sein | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e80d62f310761133a6393783eac3408178e29fd6
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184833"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklarationen von P/Invoke müssen portabel sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]
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

-   Der Rückgabewert oder Parameter als eine Ganzzahl mit fester Größe typisiert ist, wenn er als eingegeben werden, sollten eine `IntPtr`.

-   Der Rückgabewert oder Parameter als typisiert ist ein `IntPtr` Wenn typisiert als eine Ganzzahl mit fester Größe.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sie können diese Verletzung beheben, indem Sie mithilfe von `IntPtr` oder `UIntPtr` Handles anstelle von darstellen `Int32` oder `UInt32`.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
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



