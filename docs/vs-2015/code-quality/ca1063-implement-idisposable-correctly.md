---
title: 'CA1063: IDisposable korrekt implementieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ImplementIDisposableCorrectly
- CA1063
helpviewer_keywords:
- CA1063
- ImplementIDisposableCorrectly
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 90f218165c0543c1881857191efd202717c6e372
ms.sourcegitcommit: 51dad3e11d7580567673e0d426ab3b0a17584319
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/10/2019
ms.locfileid: "66820879"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable korrekt implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft.Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 `IDisposable` ist nicht ordnungsgemäß implementiert werden. Einige Ursachen dieses Problems sind hier aufgeführt:

- "IDisposable" ist neu in der Klasse implementiert.

- Finalize-erneut überschrieben wird.

- Dispose wird überschrieben.

- Dispose() ist nicht öffentlich, versiegelt oder mit dem Namen Dispose.

- Dispose(bool) ist nicht geschützten, virtuellen oder unversiegelte.

- Nicht versiegelte Typen muss Dispose(true) Dispose() aufrufen.

- Für nicht versiegelte Typen aufrufen die Finalize-Implementierung nicht eine oder beide Dispose(bool) oder den Basisklassen-Finalizer.

  Verstoß gegen eine der folgenden Muster wird diese Warnung ausgelöst.

  Jeder unversiegelte "IDisposable"-Typ muss es sich um eine eigene geschützte virtuelle "void" Dispose(bool)"-Methode bereitstellen. Dispose() sollten Dispose(true) aufrufen und Finalize Dispose(false) sollten aufrufen kann. Wenn Sie einen unversiegelte "IDisposable"-Typ erstellen, müssen Sie Dispose(bool) definieren und aufrufen. Weitere Informationen finden Sie unter [Bereinigen von nicht verwalteten Ressourcen](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) in die [Framework-Entwurfsrichtlinien](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) Abschnitt der .NET Framework-Dokumentation.

## <a name="rule-description"></a>Regelbeschreibung
 Alle IDisposable-Typen müssen das Dispose-Muster korrekt implementieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie den Code, und bestimmen Sie, welche der folgenden Lösungen diese Verletzung behoben werden.

- Entfernen Sie IDisposable aus der Liste der Schnittstellen, die von implementiert werden {0} und überschreiben Sie stattdessen die Dispose-Implementierung der Basisklasse.

- Entfernen Sie den Finalizer von Typ {0}, überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Finalize-Logik in dem Codepfad, in dem "disposing" "false".

- Entfernen Sie {0}, überschreiben Sie Dispose (Bool disposing), und platzieren Sie die Dispose-Logik in dem Codepfad, in dem "disposing" "true".

- Sicherstellen, dass {0} als öffentlich deklariert und versiegelt.

- Benennen Sie {0} in "Dispose", und stellen Sie sicher, dass es als öffentlich und versiegelt deklariert ist.

- Stellen Sie sicher, dass {0} deklariert, wie Sie geschützt haben, virtuelle und nicht versiegelt ist.

- Ändern Sie {0} , damit es Dispose(true) aufruft, ruft dann die GC. SuppressFinalize in der aktuellen Objektinstanz aufgerufen ("this" oder "Me" in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)]), und gibt dann zurück.

- Ändern Sie {0} so, dass Dispose(false) aufgerufen und gibt dann zurück.

- Wenn Sie eine unversiegelte "IDisposable"-Klasse schreiben, stellen Sie sicher, dass die Implementierung der "IDisposable" dem Muster folgt, das weiter oben in diesem Abschnitt beschrieben wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel
 Der folgende Pseudocode stellt ein allgemeines Beispiel wie Dispose(bool) implementiert werden sollte, in eine Klasse, die verwendet die verwaltete und systemeigene Ressourcen bereit.

```
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
