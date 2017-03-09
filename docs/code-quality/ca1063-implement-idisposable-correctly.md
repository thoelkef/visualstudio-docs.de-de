---
title: "CA1063: IDisposable korrekt implementieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ImplementIDisposableCorrectly"
  - "CA1063"
helpviewer_keywords: 
  - "CA1063"
  - "ImplementIDisposableCorrectly"
ms.assetid: 12afb1ea-3a17-4a3f-a1f0-fcdb853e2359
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1063: IDisposable korrekt implementieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ImplementIDisposableCorrectly|  
|CheckId|CA1063|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 `IDisposable` wurde nicht korrekt implementiert.  Zu den möglichen Gründen für dieses Problem gehören:  
  
-   IDisposable wurde in der Klasse erneut implementiert.  
  
-   Finalize wurde erneut überschrieben.  
  
-   Dispose wurde überschrieben.  
  
-   Dispose\(\) ist nicht public, sealed oder mit Dispose bezeichnet.  
  
-   Dispose\(bool\) ist nicht protected, virtual oder unsealed.  
  
-   In unversiegelten Typen muss Dispose\(\) Dispose\(true\) aufrufen.  
  
-   Bei unversiegelten Typen ruft die Finalize\-Implementierung weder Dispose\(bool\) noch den Basisklassen\-Finalizer noch beide auf.  
  
 Bei einem Verstoß gegen eines dieser Muster wird diese Warnung ausgelöst.  
  
 Jeder unversiegelte IDisposable\-Stammtyp muss eine eigene geschützte virtuelle void Dispose \(bool\)\-Methode bereitstellen.  Dispose\(\) muss Dipose\(true\) und Finalize muss Dispose\(false\) aufrufen.  Wenn Sie einen unversiegelten IDisposable\-Stammtyp erstellen, müssen Sie Dispose\(bool\) definieren und aufrufen.  Weitere Informationen finden Sie unter [Cleaning Up Unmanaged Resources](../Topic/Cleaning%20Up%20Unmanaged%20Resources.md) im Abschnitt [Framework\-Entwurfsrichtlinien](../Topic/Framework%20Design%20Guidelines.md) der Dokumentation zu .NET Framework.  
  
## Regelbeschreibung  
 Alle IDisposable\-Typen müssen das Dispose\-Muster korrekt implementieren.  
  
## Behandeln von Verstößen  
 Untersuchen Sie den Code, um festzustellen, durch welche der folgenden Lösungen dieser Verstoß behoben werden kann.  
  
-   Entfernen Sie IDisposable aus der Liste von Schnittstellen, die durch {0} implementiert wurden, und überschreiben Sie stattdessen die Dispose\-Implementierung der Basisklasse.  
  
-   Entfernen Sie den Finalizer aus dem Typ {0}, überschreiben Sie Dispose\(bool disposing\), und platzieren Sie die Finalize\-Logik in dem Codepfad, in dem 'disposing' False ist.  
  
-   Entfernen Sie {0}, überschreiben Sie Dispose\(bool disposing\), und platzieren Sie die Dispose\-Logik in dem Codepfad, in dem 'disposing' True ist.  
  
-   Vergewissern Sie sich, dass {0} als public und sealed deklariert ist.  
  
-   Benennen Sie {0} in 'Dispose' um, und vergewissern Sie sich, dass {0} als public und sealed deklariert ist.  
  
-   Vergewissern Sie sich, dass {0} als protected, virtual und unsealed deklariert ist.  
  
-   Ändern Sie {0} so, dass Dispose\(true\) und anschließend GC.SuppressFinalize in der aktuellen Objektinstanz aufgerufen \('this' oder 'Me' in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) und anschließend ein Wert zurückgegeben wird.  
  
-   Ändern Sie {0} so, dass Dispose\(false\) aufgerufen und anschließend ein Wert zurückgegeben wird.  
  
-   Wenn Sie eine unversiegelte IDisposable\-Stammklasse schreiben, stellen Sie sicher, dass die Implementierung von IDisposable dem Muster folgt, das früher in diesem Abschnitt beschrieben wird.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel für Pseudocode  
 Der folgende Pseudocode enthält ein allgemeines Beispiel für die Implementierung von Dispose\(bool\) in einer Klasse, die verwaltete und systemeigene Ressourcen verwendet.  
  
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