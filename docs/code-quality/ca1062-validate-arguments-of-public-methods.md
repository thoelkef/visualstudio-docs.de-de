---
title: "CA1062: Argumente von &#246;ffentlichen Methoden validieren | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
  - "Validate arguments of public methods"
helpviewer_keywords: 
  - "CA1062"
  - "ValidateArgumentsOfPublicMethods"
ms.assetid: db1f69ca-68f7-477e-94f3-d135cc5dfcbc
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1062: Argumente von &#246;ffentlichen Methoden validieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ValidateArgumentsOfPublicMethods|  
|CheckId|CA1062|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Eine extern sichtbare Methode dereferenziert eines der Verweisargumente, ohne zu überprüfen, ob das Argument `null` ist \(`Nothing` in Visual Basic\).  
  
## Regelbeschreibung  
 Alle an extern sichtbare Methoden übergebenen Verweisargumente sollten auf `null` überprüft werden.  Es sollte ggf. eine <xref:System.ArgumentNullException> ausgelöst werden, wenn das Argument `null` ist.  
  
 Wenn eine Methode von einer unbekannten Assembly aufgerufen werden kann, da sie als öffentlich oder geschützt deklariert wird, sollten Sie alle Parameter der Methode überprüfen.  Wenn die Methode entworfen wird, um nur von bekannten Assemblys aufgerufen zu werden, sollten Sie die Methode intern machen und das <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>\-Attribut für die Assembly übernehmen, die die Methode enthält.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, überprüfen Sie jedes Verweisargument auf `null`.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Sie können eine Warnung von dieser Regel unterdrücken, wenn Sie sicher sind, dass der dereferenzierte Parameter von einem anderen Methodenaufruf in der Funktion überprüft wurde.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die der Regel entspricht.  
  
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_1.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#1](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_1.vb)]  
  
## Beispiel  
 In [!INCLUDE[vsprvslong](../code-quality/includes/vsprvslong_md.md)] erkennt diese Regel nicht, dass Parameter an eine andere Methode übergeben werden, die die Validierung ausführt.  
  
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-cs[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/CSharp/ca1062-validate-arguments-of-public-methods_2.cs)]
 [!code-vb[FxCop.Design.ValidateArguments#2](../code-quality/codesnippet/VisualBasic/ca1062-validate-arguments-of-public-methods_2.vb)]  
  
## Beispiel  
 Kopierkonstruktoren, die Felder oder Eigenschaften auffüllen, die Verweisobjekte sind, können auch gegen die CA1062\-Regel verstoßen.  Die Verletzung tritt auf, da das kopierte Objekt, das an den Kopierkonstruktor übergeben wird, `null` sein kann \(`Nothing` in Visual Basic\).  Um die Verletzung zu beheben, verwenden Sie eine statische Methode \(freigegeben in Visual Basic\), um zu überprüfen, ob das kopierte Objekt nicht NULL ist.  
  
 Im folgenden `Person`\-Klassenbeispiel könnte das `other`\-Objekt, das an den `Person`\-Kopierkonstruktor übergeben wird `null` sein.  
  
```  
  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor CA1062 fires because other is dereferenced  
    // without being checked for null  
    public Person(Person other)  
        : this(other.Name, other.Age)  
    {  
    }  
}  
  
```  
  
## Beispiel  
 Im folgenden überprüften `Person`\-Klassenbeispiel wird das `other`\-Objekt, das an den Kopierkonstruktor übergeben wird, zuerst auf Null in der `PassThroughNonNull`\-Methode überprüft.  
  
```  
public class Person  
{  
    public string Name { get; private set; }  
    public int Age { get; private set; }  
  
    public Person(string name, int age)  
    {  
        Name = name;  
        Age = age;  
    }  
  
    // Copy constructor  
    public Person(Person other)  
        : this(PassThroughNonNull(other).Name,   
          PassThroughNonNull(other).Age)  
    {   
    }  
  
    // Null check method  
    private static Person PassThroughNonNull(Person person)  
    {  
        if (person == null)  
            throw new ArgumentNullException("person");  
        return person;  
    }  
}  
  
```