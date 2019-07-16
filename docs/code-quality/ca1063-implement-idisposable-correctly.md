---
title: 'CA1063: IDisposable korrekt implementieren.'
ms.date: 03/11/2019
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 932805f938e9d96cd944230fcc8aa82a4710da31
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820624"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable korrekt implementieren.

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

Die <xref:System.IDisposable?displayProperty=nameWithType> Schnittstelle ist nicht korrekt implementiert. Mögliche Ursachen hierfür sind:

- <xref:System.IDisposable> in der Klasse ist neu implementiert werden.

- Finalize-reoverridden ist.

- Dispose() wird überschrieben.

- Die Dispose()-Methode ist nicht öffentlich, [versiegelten](/dotnet/csharp/language-reference/keywords/sealed), oder eine benannte **Dispose**.

- Dispose(bool) ist nicht geschützten, virtuellen oder unversiegelte.

- Nicht versiegelte Typen muss Dispose(true) Dispose() aufrufen.

- Für nicht versiegelte Typen Ruft die Finalize-Implementierung eine oder beide Dispose(bool) oder den Basisklassen-Finalizer nicht.

Verstoß gegen eine der folgenden Muster löst die Warnung CA1063.

Jede nicht versiegelter Typ, der deklariert und implementiert die <xref:System.IDisposable> Schnittstelle muss eine eigene bereitstellen `protected virtual void Dispose(bool)` Methode. `Dispose()` sollten Aufrufen `Dispose(true)`, und den Aufruf des Finalizers sollten `Dispose(false)`. Wenn Sie einen nicht versiegelten Typ erstellen, die deklariert und implementiert die <xref:System.IDisposable> -Schnittstelle, die Sie definieren müssen `Dispose(bool)` und nennen Sie sie. Weitere Informationen finden Sie unter [Bereinigen nicht verwaltete Ressourcen (Handbuch für die .NET)](/dotnet/standard/garbage-collection/unmanaged) und [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern).

Diese Regel nur sucht standardmäßig an extern sichtbare Typen, aber dies ist [konfigurierbare](#configurability).

## <a name="rule-description"></a>Regelbeschreibung

Alle <xref:System.IDisposable> sollten Typen implementieren die [Dispose-Muster](/dotnet/standard/design-guidelines/dispose-pattern) ordnungsgemäß.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen

Überprüfen Sie den Code, und bestimmen Sie, welche der folgenden Lösungen diese Verletzung behoben werden:

- Entfernen Sie <xref:System.IDisposable> aus der Liste der Schnittstellen, die von Ihrem Typ implementiert werden, und überschreiben Sie stattdessen die Dispose-Implementierung der Basisklasse.

- Entfernen Sie den Finalizer aus Ihrem Typ, überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Finalize-Logik in dem Codepfad, in dem "disposing" "false".

- Überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Dispose-Logik in dem Codepfad, in dem "disposing" "true".

- Stellen Sie sicher, dass Dispose() als öffentlich deklariert wird und [versiegelten](/dotnet/csharp/language-reference/keywords/sealed).

- Benennen Sie Ihre Dispose-Methode, um **Dispose** und stellen Sie sicher, dass es als öffentlich deklariert wird und [versiegelten](/dotnet/csharp/language-reference/keywords/sealed).

- Stellen Sie sicher, dass Dispose(bool) als geschützt deklariert wird, virtuelle und nicht versiegelte.

- Dispose() so ändern, dass Dispose(true), ruft ruft dann <xref:System.GC.SuppressFinalize%2A> in der aktuellen Objektinstanz (`this`, oder `Me` in Visual Basic), und gibt dann zurück.

- Ändern Sie Ihre Finalizer, sodass Dispose(false) aufgerufen und gibt dann zurück.

- Wenn Sie einen nicht versiegelten Typ erstellen, die deklariert und implementiert die <xref:System.IDisposable> Schnittstelle, stellen Sie sicher, dass die Implementierung der <xref:System.IDisposable> folgt dem Muster, das weiter oben in diesem Abschnitt beschrieben wird.

## <a name="when-to-suppress-warnings"></a>Wenn Sie Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="configurability"></a>Konfigurierbarkeit

Wenn Sie diese Regel aus ausführen, [FxCop-Analysen](install-fxcop-analyzers.md) (und nicht über die Analyse von statischem Code), können Sie konfigurieren, welche Teile Ihrer Codebasis, um die Ausführung dieser Regel auf, um basierend auf deren Barrierefreiheit. Z. B. um anzugeben, dass die Regel nur für die nicht öffentlichen API-Oberfläche ausgeführt werden soll, fügen Sie die folgenden Schlüssel-Wert-Paar in einer editorconfig-Datei in Ihrem Projekt:

```ini
dotnet_code_quality.ca1063.api_surface = private, internal
```

Sie können diese Option, die für diese eine Regel, für alle Regeln oder für alle Regeln in dieser Kategorie (Entwurf) konfigurieren. Weitere Informationen finden Sie unter [konfigurieren FxCop-Analysetools](configure-fxcop-analyzers.md).

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

Der folgende Pseudocode stellt ein allgemeines Beispiel wie Dispose(bool) implementiert werden sollte, in eine Klasse, die verwendet die verwaltete und systemeigene Ressourcen bereit.

```csharp
public class Resource : IDisposable
{
    private IntPtr nativeResource = Marshal.AllocHGlobal(100);
    private AnotherResource managedResource = new AnotherResource();

    // Dispose() calls Dispose(true)
    public void Dispose()
    {
        Dispose(true);
        GC.SuppressFinalize(this);
    }

    // NOTE: Leave out the finalizer altogether if this class doesn't
    // own unmanaged resources, but leave the other methods
    // exactly as they are.
    ~Resource()
    {
        // Finalizer calls Dispose(false)
        Dispose(false);
    }

    // The bulk of the clean-up code is implemented in Dispose(bool)
    protected virtual void Dispose(bool disposing)
    {
        if (disposing)
        {
            // free managed resources
            if (managedResource != null)
            {
                managedResource.Dispose();
                managedResource = null;
            }
        }
        // free native resources if there are any.
        if (nativeResource != IntPtr.Zero)
        {
            Marshal.FreeHGlobal(nativeResource);
            nativeResource = IntPtr.Zero;
        }
    }
}
```

## <a name="see-also"></a>Siehe auch

- [Dispose-Muster (Framework-Entwurfsrichtlinien)](/dotnet/standard/design-guidelines/dispose-pattern)
- [Bereinigen von nicht verwalteten Ressourcen (Handbuch für die .NET)](/dotnet/standard/garbage-collection/unmanaged)