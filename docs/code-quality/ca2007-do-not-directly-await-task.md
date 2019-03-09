---
title: 'CA2007: Muss eine Aufgabe nicht direkt abgewartet'
ms.date: 03/08/2019
ms.topic: reference
f1_keywords:
- CA2007
- DoNotDirectlyAwaitATaskAnalyzer
helpviewer_keywords:
- CA2007
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.openlocfilehash: 8e94b67d1924e2144f658cd6bcd5989751efdb85
ms.sourcegitcommit: 1024f336dcd8e8a4c50b9a9ad8ec85b6e70073a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2019
ms.locfileid: "57699679"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Muss eine Aufgabe nicht direkt abgewartet

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine asynchrone Methode ["awaits"](/dotnet/csharp/language-reference/keywords/await) eine <xref:System.Threading.Tasks.Task> direkt.

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine asynchrone Methode wartet auf eine <xref:System.Threading.Tasks.Task> direkt Fortsetzung erfolgt, im gleichen Thread, der die Aufgabe erstellt. Dieses Verhalten kann die Leistung beeinträchtigen und kann dazu führen, ein Deadlock für den UI-Thread. Betrachten Sie die aufrufende <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> Ihrer Absicht für Fortsetzung zu signalisieren.

Mit dieser Regel wurden mit eingeführt [FxCop-Analysetools](install-fxcop-analyzers.md) und ist nicht vorhanden, in "Legacy" (Analyse von statischem Code) FxCop.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um Verstöße zu beheben, rufen <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> auf die erwartete <xref:System.Threading.Tasks.Task>. Sie können entweder übergeben `true` oder `false` für die `continueOnCapturedContext` Parameter.

- Aufrufen von `ConfigureAwait(true)` für den Task hat das gleiche Verhalten wie die nicht explizit aufrufen <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>. Durch explizites Aufrufen dieser Methode ein, lassen Sie die Leser wissen, dass Sie absichtlich die Fortsetzung im ursprünglichen Synchronisierungskontext ausführen möchten.

- Rufen Sie `ConfigureAwait(false)` für den Task, um Fortsetzungen an den Threadpool zu planen, einen Deadlock für den UI-Thread und vermieden. Übergeben von `false` ist eine gute Wahl für app-unabhängige Bibliotheken.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Sie können diese Warnung unterdrücken, wenn Sie wissen, dass der Consumer keine grafische Benutzeroberfläche (GUI)-app ist, oder wenn der Consumer keine <xref:System.Threading.SynchronizationContext>.

## <a name="example"></a>Beispiel

Im folgenden Codeausschnitt wird die Warnung generiert:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Um die Verletzung zu beheben, rufen <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> auf die erwartete <xref:System.Threading.Tasks.Task>:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="see-also"></a>Siehe auch

- [Sollte ich eine Aufgabe mit ConfigureAwait(false)"" await "?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installieren von FxCop-Analysen in Visual Studio](install-fxcop-analyzers.md)