---
title: 'CA1063: IDisposable korrekt implementieren'
ms.date: 02/12/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ac3827dd8ed34a118bb3e4eaaed47bf7400cef90
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2018
ms.locfileid: "31900211"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable korrekt implementieren

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache

`IDisposable` ist nicht ordnungsgemäß implementiert werden. Einige Ursachen für dieses Problem sind hier aufgeführt:

- IDisposable ist neu in der Klasse implementiert.

- Finalize erneut überschrieben wird.

- Dispose überschrieben wird.

- Dispose() ist nicht öffentlich, versiegelt oder mit dem Namen Dispose.

- Dispose(bool) ist nicht geschützten, virtuellen oder unversiegelte.

- Unversiegelte Typen muss Dispose() Dispose(true) aufrufen.

- Für unversiegelte Typen aufrufen die Finalize-Implementierung nicht eine oder beide Dispose(bool) oder den Basisklassen-Finalizer.

Verstoß gegen eine dieser Muster wird diese Warnung ausgelöst.

Jeder nicht versiegelter Typ, der deklariert und implementiert die IDisposable-Schnittstelle muss eigene geschützte virtuelle "void" Dispose(bool) Methode angeben. Dispose() muss Dipose(true) und Finalize muss Dispose(false) aufrufen. Wenn Sie einem nicht versiegelten Typs, die deklariert und implementiert die IDisposable-Schnittstelle erstellen, müssen Sie Dispose(bool) definieren und ihn aufrufen. Weitere Informationen finden Sie unter [Bereinigen von nicht verwalteten Ressourcen](/dotnet/standard/garbage-collection/unmanaged) in der [.NET Framework-Entwurfsrichtlinien](/dotnet/standard/design-guidelines/index).

## <a name="rule-description"></a>Regelbeschreibung

Alle IDisposable-Typen müssen das Dispose-Muster korrekt implementieren.

## <a name="how-to-fix-violations"></a>Behandlung von Verstößen

Überprüfen Sie den Code, und bestimmen Sie, welche der folgenden Lösungen diese Verletzung zu korrigieren.

- Entfernen Sie IDisposable aus der Liste der Schnittstellen, die von implementiert werden {0} und überschreiben Sie stattdessen die Dispose-Implementierung der Basisklasse.

- Entfernen Sie den Finalizer von Typ {0}, überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Finalize-Logik in der Codepfad, in denen "Offen" "false".

- Entfernen Sie {0}, überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Dispose-Logik in der Codepfad, in denen "Offen" "true".

- Sicherstellen, dass {0} als öffentlich deklariert und versiegelt.

- Benennen Sie {0} in 'Dispose', und stellen Sie sicher, dass es als öffentlich und versiegelt deklariert ist.

- Stellen Sie sicher, dass {0} deklariert, wie geschützte, virtuelle und nicht versiegelt ist.

- Ändern Sie {0} , damit es Dispose(true) aufruft, ruft dann GC. SuppressFinalize auf die aktuelle Objektinstanz ('this' oder 'Me' in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]), und gibt dann zurück.

- Ändern Sie {0} , damit Dispose(false) aufgerufen und gibt dann zurück.

- Wenn Sie einem nicht versiegelten Typs, die deklariert und implementiert die IDisposable-Schnittstelle erstellen, stellen Sie sicher, dass die Implementierung von IDisposable dem Muster folgt, das weiter oben in diesem Abschnitt beschrieben wird.

## <a name="when-to-suppress-warnings"></a>Wenn Warnungen unterdrücken

Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel

Der folgende Pseudocode enthält ein allgemeines Beispiel wie Dispose(bool) implementiert werden soll, in einer Klasse verwendet verwaltete und systemeigene Ressourcen.

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
    // own unmanaged resources itself, but leave the other methods
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