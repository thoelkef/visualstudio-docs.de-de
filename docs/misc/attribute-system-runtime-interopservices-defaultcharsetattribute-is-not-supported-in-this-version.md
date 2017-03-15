---
title: "Das System.Runtime.InteropServices.DefaultCharSetAttribute-Attribut wird in dieser Version nicht unterst&#252;tzt | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc32510"
  - "vbc32510"
helpviewer_keywords: 
  - "BC32510"
ms.assetid: e2eec233-6e0b-4f2f-a801-b0274e579c0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Das System.Runtime.InteropServices.DefaultCharSetAttribute-Attribut wird in dieser Version nicht unterst&#252;tzt
Mithilfe des <xref:System.Runtime.InteropServices.DefaultCharSetAttribute?displayProperty=fullName>\-Attributs können Sie den in gemarshallten Zeichenfolgen zu verwendenden Zeichensatz angeben. Es nimmt als Wert ein Member der <xref:System.Runtime.InteropServices.CharSet?displayProperty=fullName>\-Enumeration an.  
  
 Die aktuelle Version von [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] unterstützt dieses Attribut nicht. Eine Unterstützung in kommenden Versionen ist möglich.  
  
 **Fehler\-ID:** BC32510  
  
### So beheben Sie diesen Fehler  
  
-   Verwenden Sie jedes [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement), um den Zeichensatz für die deklarierte externe Prozedur anzugeben. Dies wird anhand des folgenden Beispiels veranschaulicht.  
  
    ```  
    Ansi Declare Function GetUserName Lib "advapi32.dll" _ (ByVal lpBuffer As String, ByRef nSize As Integer) As Integer Unicode Declare Sub externalProc Lib "projectlib.dll" _ (ByVal arg As Double)  
    ```  
  
     Wenn Sie den Zeichensatz in der `Declare`\-Anweisung nicht angeben, wird standardmäßig ANSI verwendet.  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.DefaultCharSetAttribute>   
 <xref:System.Runtime.InteropServices.CharSet>   
 [NICHT IM BUILD: Attribute in Visual Basic](http://msdn.microsoft.com/de-de/620bfc0e-4582-4c8b-8432-ebc5c3dccc22)   
 [Declare Statement](/dotnet/visual-basic/language-reference/statements/declare-statement)