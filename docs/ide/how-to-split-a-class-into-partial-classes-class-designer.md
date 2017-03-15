---
title: "How to: Split a Class into Partial Classes (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Class Designer, partial classes"
  - "partial classes, Class Designer"
ms.assetid: 6f6b0b30-3996-4569-9200-20482b3adf90
caps.latest.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 10
---
# How to: Split a Class into Partial Classes (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Sie können die Deklaration einer Klasse oder Struktur in Visual Basic mit dem `Partial`\-Schlüsselwort oder in Visual C\# mit dem `partial`\-Schlüsselwort auf mehrere Deklarationen verteilen.  Sie können beliebig viele partielle Deklarationen in beliebig vielen verschiedenen Quelldateien \(auch in einer\) verwenden.  Alle Deklarationen müssen jedoch in der gleichen Assembly und dem gleichen Namespace enthalten sein.  
  
 Partielle Klassen sind in mehreren Situationen nützlich.  Wenn Sie beispielsweise an großen Projekten arbeiten, können mehrere Programmierer gleichzeitig an einer Klasse arbeiten, indem Sie diese auf mehrere Dateien verteilen.  Wenn Sie mit von Visual Studio generiertem Code arbeiten, können Sie die Klasse ändern, ohne dass Sie die Quelldatei neu erstellen müssen.  \(Beispiele für von Visual Studio generierten Code sind Windows Forms und Webdienst\-Wrapper.\) Dadurch können Sie Code erstellen, der automatisch generierte Klassen verwendet, ohne die von Visual Studio erstellte Datei ändern zu müssen.  
  
 Es gibt zwei Arten von partiellen Methoden.  In Visual C\# heißen diese deklarierend und implementierend, in Visual Basic Deklaration und Implementierung.  
  
 Partielle Klassen und Methoden werden vom Klassen\-Designer unterstützt.  Die Typform im Klassendiagramm verweist auf einen einzelnen Speicherort der Deklaration für die partielle Klasse.  Wenn die partielle Klasse in mehreren Dateien definiert ist, können Sie festlegen, welcher Speicherort der Deklaration verwendet wird, indem Sie im Fenster **Eigenschaften** die Eigenschaft **Speicherort für neue Member** festlegen.  Wenn Sie also auf eine Klassenform doppelklicken, wechselt der Klassen\-Designer zu der Quelldatei, die die Klassendeklaration enthält, die durch die Eigenschaft **Speicherort für neue Member** identifiziert wird.  Wenn Sie in einer Klassenform auf eine partielle Methode doppelklicken, wechselt der Klassen\-Designer zur Deklaration der partiellen Methode, die die Klassendeklaration enthält.  Außerdem verweist im Fenster **Eigenschaften** die Eigenschaft **Dateiname** auf den Speicherort der Deklaration.  Bei partiellen Klassen werden unter **Dateiname** alle Dateien mit der Deklaration und der Implementierung dieser Klasse aufgelistet.  Bei partiellen Methoden wird unter **Dateinamen** jedoch nur die Datei aufgeführt, die die Deklaration der partiellen Methode enthält.  
  
 In den folgenden Beispielen wird die Definition der `Employee`\-Klasse auf zwei Deklarationen aufgeteilt, die jeweils eine andere Prozedur definieren.  Die beiden partiellen Definitionen aus den Beispielen können in einer Quelldatei oder in zwei unterschiedlichen Quelldateien enthalten sein.  
  
> [!NOTE]
>  Visual Basic verwendet partielle Klassendefinitionen, um Visual Studio\-generierten Code von dem Code zu trennen, der vom Benutzer erstellt wurde.  Der Code wird in einzelne Quelldateien aufgeteilt.  Zum Beispiel definiert der **Windows Form\-Designer** partielle Klassen für Steuerelemente, z. B. `Form`.  Sie sollten den generierten Code in diesen Steuerelementen nicht ändern.  
  
 Weitere Informationen über partielle Typen in Visual Basic finden Sie unter [Partial](/dotnet/visual-basic/language-reference/modifiers/partial).  
  
## Beispiel  
 Teilen Sie eine Klassendefinition in Visual Basic mit dem `Partial`\-Schlüsselwort auf, wie im folgenden Beispiel gezeigt.  
  
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
  
## Beispiel  
 Teilen Sie eine Klassendefinition in Visual C\# mit dem `partial`\-Schlüsselwort auf, wie im folgenden Beispiel gezeigt.  
  
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
  
## Siehe auch  
 [Partielle Klassen und Methoden](/dotnet/csharp/programming-guide/classes-and-structs/partial-classes-and-methods)   
 [partial \(Typ\)](/dotnet/csharp/language-reference/keywords/partial-type)   
 [partial \(Methode\) \(C\#\-Referenz\)](/dotnet/csharp/language-reference/keywords/partial-method)   
 [Partial](/dotnet/visual-basic/language-reference/modifiers/partial)