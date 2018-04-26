---
title: 'CA1060: Move P-ruft in NativeMethods-Klasse'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
helpviewer_keywords:
- MovePInvokesToNativeMethodsClass
- CA1060
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: d6035553f8d3a4518fe99e7800a61f1b5921d947
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invokes in NativeMethods-Klasse verschieben
|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode Platform Invocation Services den Zugriff auf nicht verwalteten Code verwendet und ist kein Mitglied einer der **NativeMethods** Klassen.

## <a name="rule-description"></a>Regelbeschreibung
 Plattformaufrufmethoden, beispielsweise solche, die mit markiert sind die <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> Attribut oder mithilfe von definierten Methoden der `Declare` -Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], greifen auf nicht verwalteten Code. Diese Methoden sollten in einem der folgenden Klassen angehören:

-   **NativeMethods** -unterdrückt diese Klasse nicht Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> muss diese Klasse nicht angewendet werden.) Diese Klasse ist für Methoden, die an einer beliebigen Stelle verwendet werden können, da ein Stackwalk ausgeführt wird.

-   **SafeNativeMethods** – diese Klasse unterdrückt Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> auf diese Klasse angewendet wird.) Diese Klasse ist für Methoden, die für jede Person aufrufen sicher sind. Aufrufer dieser Methoden sind zum Ausführen einer vollständigen sicherheitsüberprüfung, um sicherzustellen, dass die Verwendung sicher ist, da die Methoden für jeden Aufrufer harmlos sind nicht erforderlich.

-   **UnsafeNativeMethods** – diese Klasse unterdrückt Stackwalks Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> auf diese Klasse angewendet wird.) Diese Klasse ist für Methoden, die potenziell eine Gefahr darstellen können. Jeder Aufrufer einer dieser Methoden muss eine vollständige Sicherheit überprüfen, um sicherzustellen, dass die Verwendung sicher ist, da keine Stackwalk durchgeführt wird, ausführen.

 Diese Klassen werden als deklariert `internal` (`Friend`, in Visual Basic), und deklarieren Sie einen privaten Konstruktor zu verhindern, dass neue Instanzen erstellt werden. Die Methoden in diesen Klassen muss `static` und `internal` (`Shared` und `Friend` in Visual Basic).

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie die Methode an die entsprechende **NativeMethods** Klasse. Verschieben Sie für die meisten Anwendungen P/Invokes in eine neue Klasse mit dem Namen **NativeMethods** genügt.

 Jedoch, wenn Sie Bibliotheken zur Verwendung in anderen Anwendungen entwickeln, sollten Sie definieren zwei weitere Klassen, die aufgerufen werden **SafeNativeMethods** und **UnsafeNativeMethods**. Diese Klassen ähneln den **NativeMethods** -Klasse; allerdings markiert sind mit einem bestimmten Attribut namens **SuppressUnmanagedCodeSecurityAttribute**. Wenn dieses Attribut angewendet wird, die Laufzeit führt keine kein vollständiger Stackwalk aus, um sicherzustellen, dass alle Aufrufer die **UnmanagedCode** Berechtigung. Die Common Language Runtime überprüft in der Regel für diese Berechtigung beim Start. Da die Überprüfung nicht ausgeführt wird, dies kann erheblich verbessert die Leistung für Aufrufe dieser nicht verwalteten Methoden, erlaubt es außerdem Code, der über beschränkte Berechtigungen zum Aufrufen dieser Methoden verfügt.

 Allerdings sollten Sie dieses Attribut mit großer Umsicht verwenden. Es kann schwerwiegende sicherheitsauswirkungen haben, wenn es nicht ordnungsgemäß implementiert ist...

 Weitere Informationen dazu, wie die Methoden implementieren, finden Sie unter der **NativeMethods** beispielsweise **SafeNativeMethods** beispielsweise und **UnsafeNativeMethods** Beispiel.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Das folgende Beispiel deklariert eine Methode, die mit dieser Regel verletzt. So beheben Sie die Verletzung der **RemoveDirectory** P/Invoke in eine entsprechende-Klasse, die entwickelt wird, um nur P/Invokes halten verschoben werden soll.

 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]

## <a name="nativemethods-example"></a>NativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 Da die **NativeMethods** Klasse sollten nicht gekennzeichnet werden, mithilfe von **SuppressUnmanagedCodeSecurityAttribute**, darin P/Invokes benötigen **UnmanagedCode** Berechtigung. Da die meisten Anwendungen aus dem lokalen Computer ausgeführt werden und zusammen mit voller Vertrauenswürdigkeit ausgeführt, dies normalerweise kein Problem ist. Jedoch, wenn Sie wieder verwendbare Bibliotheken entwickeln, sollten Sie definieren eine **SafeNativeMethods** oder **UnsafeNativeMethods** Klasse.

 Das folgende Beispiel zeigt eine **Interaction.Beep** -Methode, die dient als Wrapper für die **MessageBeep** Funktion "User32.dll". Die **MessageBeep** P/Invoke ist put der **NativeMethods** Klasse.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]

## <a name="safenativemethods-example"></a>SafeNativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Invoke-Methoden, können problemlos verfügbar gemacht werden für jede Anwendung und bei denen keine Nebeneffekte, werden in einer Klasse mit dem Namen platzieren **SafeNativeMethods**. Sie müssen keine Berechtigungen fordern, und Sie müssen keine achten, wo sie aufgerufen werden.

 Das folgende Beispiel zeigt eine **Environment.TickCount** -Eigenschaft, die dient als Wrapper für die **z. B.** -Funktion von Kernel32.dll verwenden.

### <a name="code"></a>Code
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]

## <a name="unsafenativemethods-example"></a>UnsafeNativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Invoke-Methoden, die nicht sicher aufgerufen und kann, die Nebeneffekte verursachen, sollten in einer Klasse mit dem Namen **UnsafeNativeMethods**. Diese Methoden sollten gründlich überprüft werden, um sicherzustellen, dass sie nicht an den Benutzer unbeabsichtigt verfügbar gemacht werden. Die Regel [CA2118: Verwendung von SuppressUnmanagedCodeSecurityAttribute Review](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) dabei helfen können. Alternativ können Sie müssen die Methoden eine andere Berechtigung, die anstelle von gefordert wird **UnmanagedCode** Wenn sie diese verwenden.

 Das folgende Beispiel zeigt eine **Cursor.Hide** -Methode, die dient als Wrapper für die **ShowCursor** Funktion "User32.dll".

### <a name="code"></a>Code
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)