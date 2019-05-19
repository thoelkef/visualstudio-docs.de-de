---
title: 'CA2007: Eine Aufgabe nicht direkt abwarten'
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
ms.openlocfilehash: 3f35e450f17a671b800d003b94ceb5ebc2321c90
ms.sourcegitcommit: 2ee11676af4f3fc5729934d52541e9871fb43ee9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65841387"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Eine Aufgabe nicht direkt abwarten

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

## <a name="configurability"></a>Konfigurierbarkeit

Sie können konfigurieren, ob Sie asynchrone Methoden ausschließen, die von dieser Regel keinen Wert zurückgeben möchten. Um diese Arten von Methoden auszuschließen, fügen Sie folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt hinzu:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Sie können auch konfigurieren, welche Ausgabe von Arten der Assembly, die diese Regel angewendet werden soll. Z. B. hinzufügen um diese Regel nur auf Code angewendet, die eine Konsolenanwendung oder eine dynamisch verknüpfte Bibliothek (d. h. keine UI-app), erzeugt die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Siehe auch

- [Sollte ich eine Aufgabe mit ConfigureAwait(false)"" await "?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installieren von FxCop-Analysen in Visual Studio](install-fxcop-analyzers.md)