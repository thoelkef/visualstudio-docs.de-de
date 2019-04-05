---
title: 'CA1060: Verschieben von P-Invokes in NativeMethods-Klasse | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: f47fa4326da9914171e5014decbd6d6923c2f02e
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959692"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invokes in NativeMethods-Klasse verschieben.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode Platform Invocation Services den Zugriff auf nicht verwalteten Code verwendet und ist kein Mitglied eines der **NativeMethods** Klassen.

## <a name="rule-description"></a>Regelbeschreibung
 Plattformaufrufmethoden, z. B. diejenigen, die mithilfe von markiert sind die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut- oder mithilfe von definierten Methoden den `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)], Zugriff auf nicht verwalteten Code. Diese Methoden muss sich in einem der folgenden Klassen:

- **NativeMethods** -unterdrückt diese Klasse nicht Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> muss nicht auf diese Klasse angewendet werden.) Diese Klasse ist für Methoden, die an einer beliebigen Stelle verwendet werden können, da ein Stackwalk ausgeführt wird.

- **SafeNativeMethods** – diese Klasse unterdrückt Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> auf diese Klasse angewendet wird.) Diese Klasse ist für Methoden, die sicher für jeden Benutzer aufgerufen werden. Aufrufer dieser Methoden sind nicht erforderlich, um eine vollständige sicherheitsprüfung, um sicherzustellen, dass es sich bei die Verwendung sicher ist, da die Methoden für jeden Aufrufer harmlos sind auszuführen.

- **UnsafeNativeMethods** – diese Klasse unterdrückt Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> auf diese Klasse angewendet wird.) Diese Klasse ist für Methoden, die möglicherweise gefährlich sind. Jeder Aufrufer einer dieser Methoden muss eine vollständige sicherheitsprüfung, um sicherzustellen, dass es sich bei die Verwendung sicher ist, da keine Stackwalk ausgeführt wird, ausführen.

  Diese Klassen werden als deklariert `internal` (`Friend`, in Visual Basic), und deklarieren Sie einen privaten Konstruktor zu verhindern, dass neue Instanzen erstellt werden. Die Methoden in diesen Klassen muss `static` und `internal` (`Shared` und `Friend` in Visual Basic).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie die Methode an die entsprechende **NativeMethods** Klasse. Für die meisten Anwendungen, verschieben Sie P/Invokes in eine neue Klasse mit dem Namen **NativeMethods** ist ausreichend.

 Aber wenn Sie Bibliotheken für die Verwendung in anderen Anwendungen entwickeln, sollten Sie definieren zwei weitere Klassen, die aufgerufen werden **SafeNativeMethods** und **UnsafeNativeMethods**. Diese Klassen ähneln den **NativeMethods** Klasse; sie sind jedoch markiert, indem Sie ein spezielles Attribut namens **SuppressUnmanagedCodeSecurityAttribute**. Wenn dieses Attribut angewendet wird, die Laufzeit führt keine kein vollständiger Stackwalk aus, um sicherzustellen, dass alle Aufrufer haben die **UnmanagedCode** Berechtigung. Die Runtime überprüft normalerweise für diese Berechtigung beim Start. Da die Überprüfung nicht ausgeführt wird, es kann die Leistung für Aufrufe an diese nicht verwalteten Methoden erheblich verbessern, sie können zudem den Code, der über beschränkte Berechtigungen zum Aufrufen dieser Methoden verfügt.

 Allerdings sollten Sie dieses Attribut mit großer Vorsicht verwenden. Es kann ernsthafte sicherheitsauswirkungen haben, wenn es nicht ordnungsgemäß implementiert ist...

 Informationen dazu, wie die Methoden implementieren, finden Sie unter den **NativeMethods** beispielsweise **SafeNativeMethods** beispielsweise und **UnsafeNativeMethods** Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel deklariert eine Methode, die gegen diese Regel verstößt. Korrigieren Sie die Verletzung der **RemoveDirectory** P/Invoke verschoben werden soll, um eine entsprechende Klasse, die zum Speichern von P/Invokes entwickelt wurde.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>NativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 Da die **NativeMethods** Klasse sollte nicht markiert werden, mithilfe von **SuppressUnmanagedCodeSecurityAttribute**, P/Invokes, die in diese geschrieben werden müssen **UnmanagedCode** die Berechtigung. Da die meisten Anwendungen aus dem lokalen Computer ausgeführt werden und zusammen mit voller Vertrauenswürdigkeit ausgeführt werden, dies normalerweise kein Problem ist. Aber wenn Sie wiederverwendbare Bibliotheken entwickeln, sollten Sie definieren eine **SafeNativeMethods** oder **UnsafeNativeMethods** Klasse.

 Das folgende Beispiel zeigt eine **Interaction.Beep** -Methode, die dient als Wrapper für die **MessageBeep** -Funktion aus "User32.dll". Die **MessageBeep** P/Invoke ist put der **NativeMethods** Klasse.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>SafeNativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Invoke-Methoden, die sicher verfügbar gemacht werden können für jede Anwendung und die keine keine Nebeneffekte, sollten in einer Klasse mit dem Namen gesetzt werden **SafeNativeMethods**. Sie müssen keine Berechtigungen fordern, und Sie müssen nicht viel Aufmerksamkeit, in dem sie aufgerufen werden.

 Das folgende Beispiel zeigt eine **Environment.TickCount** -Eigenschaft, die dient als Wrapper für die **GetTickCount** -Funktion von kernel32.dll.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Invoke-Methoden, die nicht sicher aufgerufen und kann dazu führen, dass Nebenwirkungen, sollten in einer Klasse mit dem Namen gesetzt werden **UnsafeNativeMethods**. Diese Methoden sollten gründlich überprüft werden, um sicherzustellen, dass sie nicht an den Benutzer unbeabsichtigt verfügbar gemacht werden. Die Regel [CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute prüfen](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) dabei helfen können. Alternativ müssen die Methoden eine andere Berechtigung, die anstelle von gefordert wird **UnmanagedCode** wann diese verwendet werden.

 Das folgende Beispiel zeigt eine **Cursor.Hide** -Methode, die dient als Wrapper für die **ShowCursor** -Funktion aus "User32.dll".

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)
