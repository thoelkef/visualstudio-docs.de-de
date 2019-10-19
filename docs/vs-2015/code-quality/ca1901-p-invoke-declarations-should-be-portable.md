---
title: 'CA1901: P-Deklarationen sollten portabel sein | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
helpviewer_keywords:
- CA1901
- PInvokeDeclarationsShouldBePortable
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d1b4c0c5bcf22db6558f156fd1acd0be94026b08
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661061"
---
# <a name="ca1901-pinvoke-declarations-should-be-portable"></a>CA1901: Deklarationen von P/Invoke müssen portabel sein
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|PInvokeDeclarationsShouldBePortable|
|CheckId|CA1901|
|Kategorie|Microsoft. Portabilität|
|Unterbrechende Änderung|Unterbrechung: Wenn P/aufrufen außerhalb der Assembly sichtbar ist. Nicht unterbrechend: Wenn der P/Aufruf außerhalb der Assembly nicht sichtbar ist.|

## <a name="cause"></a>Ursache
 Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert von P/aufrufen aus und überprüft, ob ihre Größe beim Mars Hallen an nicht verwalteten Code auf 32-Bit-und 64-Bit-Plattformen korrekt ist. Der häufigste Verstoß gegen diese Regel besteht darin, eine ganze Zahl mit fester Größe zu übergeben, bei der eine Platt Form abhängige Variable mit Zeiger Größe erforderlich ist.

## <a name="rule-description"></a>Regelbeschreibung
 Beide der folgenden Szenarien verstoßen gegen diese Regel:

- Der Rückgabewert oder-Parameter wird als ganze Zahl mit fester Größe typisiert, wenn er als `IntPtr` typisiert werden soll.

- Der Rückgabewert oder-Parameter wird als `IntPtr` typisiert, wenn er als Ganzzahl mit fester Größe typisiert werden soll.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Sie können diese Verletzung beheben, indem Sie `IntPtr` oder `UIntPtr` verwenden, um Handles anstelle von `Int32` oder `UInt32` darzustellen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten diese Warnung nicht unterdrücken.

## <a name="example"></a>Beispiel
 Das folgende Beispiel veranschaulicht einen Verstoß gegen diese Regel.

```csharp
internal class NativeMethods
{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, IntPtr nIconIndex);
}
```

 In diesem Beispiel wird der `nIconIndex`-Parameter als `IntPtr` deklariert, der auf einer 32-Bit-Plattform 4 Bytes breit und auf einer 64-Bit-Plattform eine Breite von 8 Bytes hat. In der folgenden nicht verwalteten Deklaration sehen Sie, dass `nIconIndex` eine 4-Byte-Ganzzahl ohne Vorzeichen auf allen Plattformen ist.

```csharp
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,
    UINT nIconIndex);
```

## <a name="example"></a>Beispiel
 Ändern Sie die Deklaration wie folgt, um die Verletzung zu beheben:

```csharp
internal class NativeMethods{
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]
    internal static extern IntPtr ExtractIcon(IntPtr hInst,
        string lpszExeFileName, uint nIconIndex);
}
```

## <a name="see-also"></a>Siehe auch
 [Portabilitätswarnungen](../code-quality/portability-warnings.md)
