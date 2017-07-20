---
title: 'Vorgehensweise: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer) | Microsoft-Dokumentation'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Class Designer, partial classes
- partial classes, Class Designer
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 63aad78bdc7df685ca3a73ec16a9cbc87b78151f
ms.openlocfilehash: 9d74565f8e7e5b89e1716e9e2d88e2e18e077124
ms.contentlocale: de-de
ms.lasthandoff: 07/14/2017

---
# <a name="how-to-split-a-class-into-partial-classes-class-designer"></a>Gewusst wie: Aufteilen einer Klasse in partielle Klassen (Klassen-Designer)
Sie können die Deklaration einer Klasse oder Struktur auf mehrere Deklarationen aufteilen, indem Sie das `Partial`-Schlüsselwort in Visual Basic oder das `partial`-Schlüsselwort in Visual C# verwenden. Sie können beliebig viele partielle Deklarationen in beliebig vielen verschiedenen Quelldateien oder in einer Quelldatei verwenden. Alle Deklarationen müssen jedoch in der gleichen Assembly und dem gleichen Namespace enthalten sein.  
  
 Partielle Klassen sind in vielen Situationen nützlich. Wenn Sie z.B. an großen Projekten arbeiten, können durch Aufteilen einer Klasse in mehr als eine Datei mehrere Programmierer gleichzeitig an diesem Projekt arbeiten. Wenn Sie mit Code arbeiten, der von Visual Studio erstellt wird, können Sie die Klasse ändern, ohne die Quelldatei erneut erstellen zu müssen. (Beispiele von Code, der von Visual Studio erstellt sind u.A. Windows Forms-Code und Webdienst-Wrappercode.) Sie können deshalb Code erstellen, der diese automatisch generierte Klassen verwendet, ohne die von Visual Studio erstellte Datei ändern zu müssen.  
  
 Es gibt zwei Arten von partiellen Methoden. In Visual C# werden Sie deklarierende und implementierende Methoden genannt. In Visual Basic heißen sie Deklaration und Implementierung.  
  
 Der Klassen-Designer unterstützt partielle Klassen und Methoden. Die Typform im Klassendiagramm bezieht sich auf einen einzelnen Deklarationsort für die partielle Klasse. Wenn die partielle Klasse in mehreren Dateien definiert ist, können Sie angeben, welchen Deklarationsort der Klassen-Designer durch Festlegen der Eigenschaft **Speicherort für neue Member** im Fenster **Eigenschaften** verwenden wird. Das heißt, wenn Sie einen Doppelklick auf eine Klassenform ausführen, wechselt der Klassen-Designer zur Quelldatei, die die Klassendeklaration enthält, die von der Eigenschaft **Speicherort für neue Member** identifiziert ist. Wenn Sie einen Doppelklick auf eine partielle Methode in einer Klassenform ausführen, wechselt der Klassen-Designer zur Deklaration der partiellen Methode. Im Fenster **Eigenschaften** bezieht sich die Eigenschaft **Dateiname** ebenso auf den Speicherort der Deklaration. Für partielle Klassen führt der **Dateiname** alle Dateien auf, die Deklarations- und Implementierungscode für diese Klasse enthalten. Für partielle Methoden listet der **Dateiname** jedoch nur die Datei auf, die die Deklaration der partiellen Methode enthält.  
  
 In den folgenden Beispielen wird die Definition der `Employee`-Klasse auf zwei Deklarationen aufgeteilt, die jeweils eine andere Prozedur definieren. Die beiden partiellen Definitionen aus dem Beispiel können in einer Quelldatei oder in zwei unterschiedlichen Quelldateien enthalten sein.  
  
> [!NOTE]
>  Visual Basic verwendet partielle Klassendefinitionen, um generierten Code von Visual Studio von Code zu trennen, der vom Benutzer erstellt wurde. Der Code wird in diskrete Quelldateien aufgeteilt. Zum Beispiel definiert der **Windows Form-Designer** partielle Klassen für Steuerelemente, z.B. `Form`. Sie sollten den generierten Code in diesen Steuerelementen nicht ändern.  
  
 Weitere Informationen über partielle Typen in Visual Basic finden Sie unter [Partial (Partiell)](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## <a name="example"></a>Beispiel  
 Verwenden Sie zum Aufteilen einer Klassendefinition in Visual Basic das Schlüsselwort `Partial`, so wie in folgendem Beispiel dargestellt.  
  
```vb#  
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
  
```c#  
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
  
## <a name="see-also"></a>Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial (Typ)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partial (Methode) (C#-Referenz)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)
