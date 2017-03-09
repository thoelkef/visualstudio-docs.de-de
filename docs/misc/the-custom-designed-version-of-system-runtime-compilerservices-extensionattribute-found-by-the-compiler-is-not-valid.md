---
title: "Die vom Compiler gefundene benutzerdefinierte Version von „System.Runtime.CompilerServices.ExtensionAttribute“ ist nicht g&#252;ltig. | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc36558"
  - "bc36558"
helpviewer_keywords: 
  - "BC36558"
ms.assetid: f47d310a-95fd-4340-bda2-21262c217dbb
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Die vom Compiler gefundene benutzerdefinierte Version von „System.Runtime.CompilerServices.ExtensionAttribute“ ist nicht g&#252;ltig.
Die vom Compiler gefundene benutzerdefinierte Version von „System.Runtime.CompilerServices.ExtensionAttribute“ ist nicht gültig. Die Flags für die Attributverwendung müssen so festgelegt sein, dass Assemblys, Klassen und Methoden zulässig sind.  
  
 Die vom Compiler gefundene benutzerdefinierte Version von <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> legt ihre Flags für die Attributverwendung nicht fest, um die Anwendung des Attributs auf Assemblys, Methoden und Klassen zu aktivieren. Die Anwendung auf mindestens drei Programmelemente ist erforderlich.  
  
 **Fehler\-ID:** BC36558  
  
### So beheben Sie diesen Fehler  
  
-   Ändern Sie die Attributdefinition, um die Anwendung des Attributs wenigstens auf Assemblys, Methoden und Klassen zu aktivieren, wie in den folgenden Beispielen gezeigt.  
  
-   Verwenden Sie <xref:System.Runtime.CompilerServices.ExtensionAttribute?displayProperty=fullName> anstelle der benutzerdefinierten Version.  
  
## Beispiel  
 Im folgenden Beispiel wird das `AttributeUsage`\-Attribut verwendet, um anzugeben, auf welche Programmelemente die neue Version von `ExtensionAttribute` angewendet werden kann. Das Beispiel gibt drei Member der `AttributeTargets`\-Enumeration an: `Assembly`, `Class` und `Method`. Die Auslassung eines dieser Elemente verursacht diesen Fehler.  
  
```  
Namespace System.Runtime.CompilerServices <AttributeUsage(AttributeTargets.Assembly Or _ AttributeTargets.Class Or AttributeTargets.Method)> Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
 Alternativ können Sie `ExtensionAttribute` die Anwendung auf alle Programmelemente mithilfe des `All`\-Members von `AttributeTargets` gestatten.  
  
```  
<AttributeUsage(AttributeTargets.All)>  
```  
  
 Das Löschen der `AttributeUsage`\-Zeile führt zum gleichen Ergebnis, wie im folgenden Code gezeigt.  
  
```  
Namespace System.Runtime.CompilerServices Class ExtensionAttribute Inherits System.Attribute ' Definitions of methods, fields, and properties. End Class End Namespace  
```  
  
## Siehe auch  
 <xref:System.Runtime.CompilerServices.ExtensionAttribute>   
 [NICHT IM BUILD: Übersicht über Attribute in Visual Basic](http://msdn.microsoft.com/de-de/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NICHT IM BUILD: Benutzerdefinierte Attribute in Visual Basic](http://msdn.microsoft.com/de-de/d72d8a5c-8f64-4614-b15b-cad66845d047)   
 [Erweiterungsmethoden](/dotnet/visual-basic/programming-guide/language-features/procedures/extension-methods)   
 [NICHT IM BUILD: Gewusst wie: Definieren eigener Attribute](http://msdn.microsoft.com/de-de/039609c4-ec43-4f44-945f-aa3b5b535c6a)   
 [Verfassen von benutzerdefinierten Attributen](../Topic/Writing%20Custom%20Attributes.md)