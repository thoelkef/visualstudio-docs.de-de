---
title: 'CA1060: P-Aufrufe in die NativeMethods-Klasse verschieben | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 49a693224b6552340d2a01051318842749a84cc1
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663677"
---
# <a name="ca1060-move-pinvokes-to-nativemethods-class"></a>CA1060: P/Invokes in NativeMethods-Klasse verschieben
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MovePInvokesToNativeMethodsClass|
|CheckId|CA1060|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine Methode verwendet Platt Form Aufruf Dienste für den Zugriff auf nicht verwalteten Code und ist nicht Mitglied einer der **NativeMethods** -Klassen.

## <a name="rule-description"></a>Regelbeschreibung
 Platt Form Aufruf Methoden, wie z. b. solche, die mit dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>-Attribut gekennzeichnet sind, oder Methoden, die mit dem Schlüsselwort `Declare` in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] definiert werden, greifen auf nicht verwalteten Code zu. Diese Methoden sollten einer der folgenden Klassen unterliegen:

- **NativeMethods** : Diese Klasse unterdrückt keine Stapel Spaziergänge für die Berechtigung "nicht verwalteter Code". (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> darf nicht auf diese Klasse angewendet werden.) Diese Klasse eignet sich für Methoden, die überall verwendet werden können, da ein Stackwalk ausgeführt wird.

- **Safsativemethods** : Diese Klasse unterdrückt Stapel Spaziergänge für die Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> wird auf diese Klasse angewendet.) Diese Klasse eignet sich für Methoden, die für jeden aufzurufenden Benutzer sicher sind. Aufrufer dieser Methoden müssen keine vollständige Sicherheitsüberprüfung durchführen, um sicherzustellen, dass die Verwendung sicher ist, da die Methoden für jeden Aufrufer harmlos sind.

- **Unsaftenativemethods** : Diese Klasse unterdrückt Stapel Spaziergänge für die Berechtigung für nicht verwalteten Code. (<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> wird auf diese Klasse angewendet.) Diese Klasse ist für Methoden, die potenziell gefährlich sind. Alle Aufrufer dieser Methoden müssen eine vollständige Sicherheitsüberprüfung durchführen, um sicherzustellen, dass die Nutzung sicher ist, da keine Stapelausführung durchgeführt wird.

  Diese Klassen werden als `internal` (`Friend` in Visual Basic) deklariert und deklarieren einen privaten Konstruktor, um zu verhindern, dass neue Instanzen erstellt werden. Die Methoden in diesen Klassen sollten `static` und `internal` (`Shared` und `Friend` in Visual Basic) sein.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie die Methode in die entsprechende **NativeMethods** -Klasse. Bei den meisten Anwendungen ist das Verschieben von P/aufrufen in eine neue Klasse mit dem Namen **NativeMethods** ausreichend.

 Wenn Sie jedoch Bibliotheken für die Verwendung in anderen Anwendungen entwickeln, sollten Sie zwei andere Klassen definieren, die als **SafeNativeMethods** und **UnsafeNativeMethods**bezeichnet werden. Diese Klassen ähneln der **NativeMethods** -Klasse. Sie werden jedoch mit einem speziellen Attribut namens **SuppressUnmanagedCodeSecurityAttribute**markiert. Wenn dieses Attribut angewendet wird, führt die Laufzeit keinen vollständigen Stapel Durchlauf aus, um sicherzustellen, dass alle Aufrufer über die **UnmanagedCode** -Berechtigung verfügen. Die Laufzeit prüft diese Berechtigung normalerweise beim Start. Da die Überprüfung nicht durchgeführt wird, kann Sie die Leistung für Aufrufe dieser nicht verwalteten Methoden erheblich verbessern. Sie ermöglicht auch Code mit eingeschränkten Berechtigungen zum Aufrufen dieser Methoden.

 Sie sollten dieses Attribut jedoch sehr sorgfältig verwenden. Dies kann schwerwiegende Auswirkungen auf die Sicherheit haben, wenn es nicht ordnungsgemäß implementiert wird.

 Weitere Informationen zum Implementieren der Methoden finden Sie in den Beispielen für **NativeMethods** , **SafeNativeMethods** und **UnsafeNativeMethods** .

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="example"></a>Beispiel
 Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt. Um die Verletzung zu beheben, sollte das **RemoveDirectory** -P/-aufrufen in eine geeignete Klasse verschoben werden, die nur P/Aufrufe enthalten soll.

 [!code-csharp[FxCop.Design.DllImportNativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/cs/FxCop.Design.DllImportNativeMethods.cs#1)]
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.DllImportNativeMethods/vb/FxCop.Design.DllImportNativeMethods.vb#1)]

## <a name="nativemethods-example"></a>NativeMethods-Beispiel

### <a name="description"></a>Beschreibung
 Da die **NativeMethods** -Klasse nicht mithilfe von **SuppressUnmanagedCodeSecurityAttribute**gekennzeichnet werden sollte, benötigen Sie die **UnmanagedCode** -Berechtigung. Da die meisten Anwendungen auf dem lokalen Computer ausgeführt werden und mit voller Vertrauenswürdigkeit ausgeführt werden, ist dies in der Regel kein Problem. Wenn Sie jedoch wiederverwendbare Bibliotheken entwickeln, sollten Sie die Definition einer **safeativemethods** -Klasse oder einer **unsafsativemethods** -Klasse in Erwägung gezogen.

 Im folgenden Beispiel wird eine **Interaktion. Beep** -Methode gezeigt, die die **MessageBeep** -Funktion von user32. dll umschließt. Der **MessageBeep** -P/-Aufruf wird in die **NativeMethods** -Klasse eingefügt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethods#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/cs/FxCop.Design.NativeMethods.cs#1)]
 [!code-vb[FxCop.Design.NativeMethods#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethods/vb/FxCop.Design.NativeMethods.vb#1)]

## <a name="safenativemethods-example"></a>Safumativemethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Aufrufen von Methoden, die auf sichere Weise für jede Anwendung verfügbar gemacht werden können und die keine Nebeneffekte haben, sollten in einer Klasse mit dem Namen **SafeNativeMethods**abgelegt werden. Sie müssen keine Berechtigungen anfordern, und Sie müssen nicht mehr darauf achten, wo Sie von aufgerufen werden.

 Das folgende Beispiel zeigt eine **Environment. TickCount** -Eigenschaft, die die **GetTickCount** -Funktion von Kernel32. dll umschließt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethodsSafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/cs/FxCop.Design.NativeMethodsSafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsSafe/vb/FxCop.Design.NativeMethodsSafe.vb#1)]

## <a name="unsafenativemethods-example"></a>Unsafumativemethods-Beispiel

### <a name="description"></a>Beschreibung
 P/Aufrufen von Methoden, die nicht sicher aufgerufen werden können und die Nebeneffekte verursachen könnten, sollten in einer Klasse mit dem Namen **unsafdenativemethods**abgelegt werden. Diese Methoden sollten streng geprüft werden, um sicherzustellen, dass Sie nicht versehentlich für den Benutzer verfügbar gemacht werden. Die Regel [CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) kann dazu beitragen. Alternativ dazu sollten die Methoden eine andere Berechtigung aufweisen, die anstelle von **UnmanagedCode** angefordert wird, wenn Sie Sie verwenden.

 Das folgende Beispiel zeigt eine **Cursor. Hide** -Methode, die die **ShowCursor** -Funktion von user32. dll umschließt.

### <a name="code"></a>Code
 [!code-csharp[FxCop.Design.NativeMethodsUnsafe#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/cs/FxCop.Design.NativeMethodsUnsafe.cs#1)]
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.NativeMethodsUnsafe/vb/FxCop.Design.NativeMethodsUnsafe.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Entwurfswarnungen](../code-quality/design-warnings.md)
