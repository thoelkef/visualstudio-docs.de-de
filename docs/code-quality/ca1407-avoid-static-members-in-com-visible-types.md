---
title: "CA1407: Statische Member in f&#252;r COM sichtbaren Typen vermeiden | Microsoft Docs"
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
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
helpviewer_keywords: 
  - "CA1407"
  - "AvoidStaticMembersInComVisibleTypes"
ms.assetid: bebd0776-ad04-453c-bca8-8c124c2d7840
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1407: Statische Member in f&#252;r COM sichtbaren Typen vermeiden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidStaticMembersInComVisibleTypes|  
|CheckId|CA1407|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Typ, der ausdrücklich als für Component Object Model \(COM\) sichtbar markiert ist, enthält eine `public` `static` Methode.  
  
## Regelbeschreibung  
 COM unterstützt keine `static`\-Methoden.  
  
 Bei der Überprüfung dieser Regel werden Eigenschaften\- und Ereignisaccessoren, Methoden für Operatorüberladungen oder mit dem <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute?displayProperty=fullName>\-Attribut oder dem <xref:System.Runtime.InteropServices.ComUnregisterFunctionAttribute?displayProperty=fullName>\-Attribut markierte Methoden ignoriert.  
  
 Standardmäßig sind folgende Programmierelemente für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member öffentlicher Werttypen.  
  
 Damit diese Regel eintritt, müssen ein <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf Assemblyebene auf `false` und das <xref:System.Runtime.InteropServices.ComVisibleAttribute> auf Klassenebene auf `true` festgelegt werden. Siehe dazu folgendes Codebeispiel:  
  
```c#  
using System;  
using System.Runtime.InteropServices;   
  
[assembly: ComVisible(false)]   
namespace Samples  
{      
    [ComVisible(true)]  
    public class MyClass  
    {  
        public static void DoSomething()  
        {  
        }  
    }  
}  
```  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ändern Sie das Design dahingehend, dass eine Instanzenmethode verwendet wird, die die gleiche Funktionalität wie die `static`\-Methode bereitstellt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn ein COM\-Client nicht auf die von der `static`\-Methode bereitgestellte Funktionalität zugreifen muss.  
  
## Beispiel für einen Verstoß  
  
### **Beschreibung**  
 Im folgenden Beispiel wird eine `static`\-Methode veranschaulicht, die gegen diese Regel verstößt.  
  
### Code  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersViolation#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_1.cs)]  
  
### Kommentare  
 Im folgenden Beispiel kann die **Book.FromPages**\-Methode nicht aus COM aufgerufen werden.  
  
## Beispiel für die Behandlung  
  
### **Beschreibung**  
 Um den Verstoß im vorigen Beispiel zu behandeln, könnten Sie die Methode in eine Instanzenmethode ändern, was in diesem Fall jedoch keinen Sinn ergibt.  Eine bessere Lösung besteht darin, `ComVisible(false)` explizit auf die Methode anzuwenden, um anderen Entwicklern gegenüber zu verdeutlichen, dass die Methode nicht aus COM angezeigt werden kann.  
  
 Im folgenden Beispiel wird <xref:System.Runtime.InteropServices.ComRegisterFunctionAttribute> auf die Methode angewendet.  
  
### Code  
 [!code-cs[FxCop.Interoperability.ComVisibleStaticMembersFixed#1](../code-quality/codesnippet/CSharp/ca1407-avoid-static-members-in-com-visible-types_2.cs)]  
  
## Verwandte Regeln  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
 [CA1406: Int64\-Argumente für Visual Basic 6\-Clients vermeiden](../code-quality/ca1406-avoid-int64-arguments-for-visual-basic-6-clients.md)  
  
 [CA1413: Nicht öffentliche Felder in für COM sichtbaren Werttypen vermeiden](../code-quality/ca1413-avoid-non-public-fields-in-com-visible-value-types.md)  
  
## Siehe auch  
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)