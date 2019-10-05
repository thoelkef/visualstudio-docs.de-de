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
ms.openlocfilehash: cf07c997f933e6aacf3eff29ae204ecd0bedb036
ms.sourcegitcommit: 0c2523d975d48926dd2b35bcd2d32a8ae14c06d8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/24/2019
ms.locfileid: "71233073"
---
# <a name="ca2007-do-not-directly-await-a-task"></a>CA2007: Eine Aufgabe nicht direkt abwarten

|||
|-|-|
|TypeName|DoNotDirectlyAwaitATaskAnalyzer|
|CheckId|CA2007|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Eine asynchrone Methode [erwartet](/dotnet/csharp/language-reference/keywords/await) direkt <xref:System.Threading.Tasks.Task> ein.

## <a name="rule-description"></a>Regelbeschreibung

Wenn eine asynchrone Methode direkt auf <xref:System.Threading.Tasks.Task> einen wartet, erfolgt die Fortsetzung in dem Thread, der die Aufgabe erstellt hat. Dieses Verhalten kann sich in Bezug auf die Leistung als kostspielig erweisen und kann zu einem Deadlock im UI-Thread führen. Rufen <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> Sie auf, um ihre Absicht für die Fortsetzung zu signalisieren.

Diese Regel wurde mit [FxCop-Analyzern](install-fxcop-analyzers.md) eingeführt und ist nicht in der Legacy-FxCop-Analyse vorhanden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Um Verstöße zu beheben, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> wenden Sie auf <xref:System.Threading.Tasks.Task>den erwarteten an. Sie können entweder `true` oder `false` für den `continueOnCapturedContext` -Parameter übergeben.

- Das `ConfigureAwait(true)` Aufrufen von für die Aufgabe hat das gleiche Verhalten wie das <xref:System.Threading.Tasks.Task.ConfigureAwait%2A>explizite Aufrufen von. Wenn Sie diese Methode explizit aufrufen, können Sie den Lesern mitteilen, dass Sie absichtlich die Fortsetzung im ursprünglichen Synchronisierungs Kontext ausführen möchten.

- Ruft `ConfigureAwait(false)` für den Task auf, um Fortsetzungen für den Thread Pool zu planen und so einen Deadlock im UI-Thread zu vermeiden. Die `false` Übergabe ist eine gute Option für App-unabhängige Bibliotheken.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?

Sie können diese Warnung unterdrücken, wenn Sie wissen, dass es sich bei dem Consumer nicht um eine grafische Benutzeroberfläche (GUI) handelt oder wenn <xref:System.Threading.SynchronizationContext>der Consumer keinen hat.

## <a name="example"></a>Beispiel

Der folgende Code Ausschnitt generiert die Warnung:

```csharp
public async Task Execute()
{
    Task task = null;
    await task;
}
```

Um die Verletzung zu beheben, <xref:System.Threading.Tasks.Task.ConfigureAwait%2A> wenden Sie auf <xref:System.Threading.Tasks.Task>den erwarteten an:

```csharp
public async Task Execute()
{
    Task task = null;
    await task.ConfigureAwait(false);
}
```

## <a name="configurability"></a>Konfigurierbarkeit

Sie können konfigurieren, ob Sie asynchrone Methoden ausschließen möchten, die keinen Wert aus dieser Regel zurückgeben. Fügen Sie das folgende Schlüssel-Wert-Paar in eine editorconfig-Datei in Ihrem Projekt ein, um diese Arten von Methoden auszuschließen:

```ini
# Package version 2.9.0 and later
dotnet_code_quality.CA2007.exclude_async_void_methods = true

# Package version 2.6.3 and earlier
dotnet_code_quality.CA2007.skip_async_void_methods = true
```

Sie können auch konfigurieren, auf welche ausgabeassemblyarten diese Regel angewendet werden soll. Fügen Sie z. b. das folgende Schlüssel-Wert-Paar zu einer Editor config-Datei in Ihrem Projekt hinzu, um diese Regel nur auf Code anzuwenden, der eine Konsolenanwendung oder eine dynamisch verknüpfte Bibliothek erstellt (d. h. keine UI-APP):

```ini
dotnet_code_quality.CA2007.output_kind = ConsoleApplication, DynamicallyLinkedLibrary
```

Weitere Informationen finden Sie unter [Konfigurieren von FxCop-Analysen](configure-fxcop-analyzers.md).

## <a name="see-also"></a>Siehe auch

- [Sollte ich auf eine Aufgabe mit "Konfigurieren" (falsch) warten?](https://github.com/Microsoft/vs-threading/blob/master/doc/cookbook_vs.md#should-i-await-a-task-with-configureawaitfalse)
- [Installieren von FxCop-Analyzern in Visual Studio](install-fxcop-analyzers.md)