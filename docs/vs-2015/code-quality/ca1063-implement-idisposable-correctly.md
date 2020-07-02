---
title: 'CA1063: iverwerfkorrekt implementieren | Microsoft-Dokumentation'
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
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 04691d2344b232906676180122ad67fff5405891
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/30/2020
ms.locfileid: "85539359"
---
# <a name="ca1063-implement-idisposable-correctly"></a>CA1063: IDisposable korrekt implementieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ImplementIDisposableCorrectly|
|CheckId|CA1063|
|Kategorie|Microsoft. Design|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 `IDisposable`ist nicht ordnungsgemäß implementiert. Einige Gründe für dieses Problem sind hier aufgeführt:

- Iverwerfist in der-Klasse neu implementiert.

- Finalize wird erneut überschrieben.

- Verwerfen wird überschrieben.

- Verwerfen () ist nicht öffentlich, versiegelt oder benannt.

- Verwerfen (bool) ist nicht geschützt, virtuell oder nicht versiegelt.

- Bei nicht versiegelten Typen muss verwerfen () "verwerfen (true)" aufgerufen werden.

- Bei nicht versiegelten Typen Ruft die Finalize-Implementierung weder den Löschvorgang (bool) noch den Case-Klassen-Finalizer auf.

  Eine Verletzung eines dieser Muster löst diese Warnung aus.

  Alle nicht versiegelten root-iverwerf-Typen müssen eine eigene geschützte Methode für die virtuelle void-Freigabe (bool) bereitstellen. Verwerfen () sollte "verwerfen (true)" und "Finalize" den Befehl "verwerfen (false)" aufzurufen. Wenn Sie einen nicht versiegelten Stamm-iverwerf-Typ erstellen, müssen Sie verwerfen (bool) definieren und ihn anrufen. Weitere Informationen finden Sie im Abschnitt zum [Bereinigen nicht verwalteter Ressourcen](https://msdn.microsoft.com/library/a17b0066-71c2-4ba4-9822-8e19332fc213) im Abschnitt [Framework-Entwurfs Richtlinien](https://msdn.microsoft.com/library/5fbcaf4f-ea2a-4d20-b0d6-e61dee202b4b) in der .NET Framework-Dokumentation.

## <a name="rule-description"></a>Beschreibung der Regel
 Alle IDisposable-Typen müssen das Dispose-Muster korrekt implementieren.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Überprüfen Sie den Code, und legen Sie fest, welche der folgenden Auflösungen diese Verletzung beheben soll.

- Entfernen Sie iverwerfaus der Liste der Schnittstellen, die von implementiert werden, {0} und überschreiben Sie stattdessen die b-Implementierung der Basisklasse.

- Entfernen Sie den Finalizer aus dem Typ, überschreiben Sie verwerfen {0} (bool disposing), und platzieren Sie die finalisierungslogik in den Codepfad, in dem "disposing" "false" ist.

- Entfernen Sie, überschreiben Sie verwerfen {0} (bool disposing), und platzieren Sie die Lösch Logik in den Codepfad, in dem "disposing" "true" ist.

- Stellen Sie sicher, dass {0} als öffentlich und versiegelt deklariert ist.

- Benennen {0} Sie in "verwerfen" um, und stellen Sie sicher, dass es als öffentlich und versiegelt deklariert ist.

- Stellen Sie sicher, dass {0} als geschützt, virtuell und nicht versiegelt deklariert ist.

- Ändern {0} Sie, damit "verwerfen (true)" aufgerufen wird, und rufen Sie dann GC auf. SuppressFinalize auf der aktuellen Objektinstanz ("This" oder "Me" in [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] ), und gibt dann zurück.

- Ändern {0} Sie, sodass verwerfen (false) aufgerufen wird, und gibt dann zurück.

- Wenn Sie eine nicht versiegelte iverwerf-Stamm Klasse schreiben, stellen Sie sicher, dass die Implementierung von iverwerfdas Muster befolgt, das weiter oben in diesem Abschnitt beschrieben wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel.

## <a name="pseudo-code-example"></a>Pseudocodebeispiel
 Der folgende Pseudo Code bietet ein allgemeines Beispiel dafür, wie "verwerfen (bool)" in einer Klasse implementiert werden sollte, die verwaltete und Native Ressourcen verwendet.

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
