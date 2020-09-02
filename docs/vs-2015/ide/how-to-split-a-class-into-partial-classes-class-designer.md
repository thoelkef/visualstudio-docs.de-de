---
title: 'Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer) | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e93ebc58e4e9b6092921e4155fe3d821bb552c7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670716"
---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Gewusst wie: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Sie können die Deklaration einer Klasse oder Struktur auf mehrere Deklarationen aufteilen, indem Sie das `Partial`-Schlüsselwort in Visual Basic oder das `partial`-Schlüsselwort in Visual C# verwenden. Sie können beliebig viele partielle Deklarationen in beliebig vielen verschiedenen Quelldateien oder in einer Quelldatei verwenden. Alle Deklarationen müssen jedoch in der gleichen Assembly und dem gleichen Namespace enthalten sein.

 Partielle Klassen sind in vielen Situationen nützlich. Wenn Sie z.B. an großen Projekten arbeiten, können durch Aufteilen einer Klasse in mehr als eine Datei mehrere Programmierer gleichzeitig an diesem Projekt arbeiten. Wenn Sie mit Code arbeiten, der von Visual Studio erstellt wird, können Sie die Klasse ändern, ohne die Quelldatei erneut erstellen zu müssen. (Beispiele für Code, der von Visual Studio generiert wird, sind Windows Forms-und Webdienst-Wrapper Code.) Auf diese Weise können Sie Code erstellen, der automatisch generierte Klassen verwendet, ohne die von Visual Studio erstellte Datei ändern zu müssen.

 Es gibt zwei Arten von partiellen Methoden. In Visual C# werden Sie deklarierende und implementierende Methoden genannt. In Visual Basic heißen sie Deklaration und Implementierung.

 Der Klassen-Designer unterstützt partielle Klassen und Methoden. Die Typform im Klassendiagramm bezieht sich auf einen einzelnen Deklarationsort für die partielle Klasse. Wenn die partielle Klasse in mehreren Dateien definiert ist, können Sie angeben, welchen Deklarationsort der Klassen-Designer durch Festlegen der Eigenschaft **Speicherort für neue Member** im Fenster **Eigenschaften** verwenden wird. Das heißt, wenn Sie einen Doppelklick auf eine Klassenform ausführen, wechselt der Klassen-Designer zur Quelldatei, die die Klassendeklaration enthält, die von der Eigenschaft **Speicherort für neue Member** identifiziert ist. Wenn Sie einen Doppelklick auf eine partielle Methode in einer Klassenform ausführen, wechselt der Klassen-Designer zur Deklaration der partiellen Methode. Im Fenster **Eigenschaften** bezieht sich die Eigenschaft **Dateiname** ebenso auf den Speicherort der Deklaration. Für partielle Klassen führt der **Dateiname** alle Dateien auf, die Deklarations- und Implementierungscode für diese Klasse enthalten. Für partielle Methoden listet der **Dateiname** jedoch nur die Datei auf, die die Deklaration der partiellen Methode enthält.

 In den folgenden Beispielen wird die Definition der `Employee`-Klasse auf zwei Deklarationen aufgeteilt, die jeweils eine andere Prozedur definieren. Die beiden partiellen Definitionen aus dem Beispiel können in einer Quelldatei oder in zwei unterschiedlichen Quelldateien enthalten sein.

> [!NOTE]
> Visual Basic verwendet partielle Klassendefinitionen, um generierten Code von Visual Studio von Code zu trennen, der vom Benutzer erstellt wurde. Der Code wird in diskrete Quelldateien aufgeteilt. Zum Beispiel definiert der **Windows Form-Designer** partielle Klassen für Steuerelemente, z.B. `Form`. Sie sollten den generierten Code in diesen Steuerelementen nicht ändern.

 Weitere Informationen über partielle Typen in Visual Basic finden Sie unter [Partial (Partiell)](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448).

## <a name="example"></a>Beispiel
 Verwenden Sie zum Aufteilen einer Klassendefinition in Visual Basic das Schlüsselwort `Partial`, so wie in folgendem Beispiel dargestellt.

```vb
' First part of class definition.
Partial Public Class Employee
    Public Sub CalculateWorkHours()
    End Sub
End Class

' Second part of class definition.
Partial Public Class Employee
    Public Sub CalculateTaxes()
    End Sub
End Class
```

## <a name="example"></a>Beispiel
 Verwenden Sie zum Aufteilen einer Klassendefinition in Visual C# das Schlüsselwort `partial`, so wie in folgendem Beispiel dargestellt.

```csharp
// First part of class definition.
public partial class Employee
{
    public void CalculateWorkHours()
    {
    }
}

// Second part of class definition.
public partial class Employee
{
    public void CalculateTaxes()
    {
    }
}
```

## <a name="see-also"></a>Weitere Informationen
 Partielle [Klassen und Methoden](https://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1) [partiell (Typ)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334) [partiell (Methode) (c#-Referenz)](https://msdn.microsoft.com/library/43f40242-17e0-4452-8573-090503ad3137) [partiell](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448)
