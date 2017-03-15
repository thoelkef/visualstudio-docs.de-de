---
title: "CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren | Microsoft Docs"
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
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
helpviewer_keywords: 
  - "CA1414"
  - "MarkBooleanPInvokeArgumentsWithMarshalAs"
ms.assetid: c0c84cf5-7701-4897-9114-66fc4b895699
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1414: Boolesche P/Invoke-Argumente mit MarshalAs markieren
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkBooleanPInvokeArgumentsWithMarshalAs|  
|CheckId|CA1414|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Deklaration für eine Plattformaufrufmethode enthält einen <xref:System.Boolean?displayProperty=fullName>\-Parameter oder \-Rückgabewert, allerdings wird das <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=fullName>\-Attribut nicht auf den Parameter oder Rückgabewert angewendet.  
  
## Regelbeschreibung  
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code zu und wird mit dem `Declare`\-Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> definiert.  <xref:System.Runtime.InteropServices.MarshalAsAttribute> gibt das Marshallingverhalten an, das verwendet wurde, um Datentypen zwischen verwaltetem und nicht verwaltetem Code zu konvertieren.  Für viele einfache Datentypen wie <xref:System.Byte?displayProperty=fullName> und <xref:System.Int32?displayProperty=fullName> ist eine einzige Darstellung in nicht verwaltetem Code vorhanden, und daher muss ihr Marshallingverhalten nicht angegeben werden. Die Common Language Runtime stellt automatisch das richtige Verhalten bereit.  
  
 Der <xref:System.Boolean>\-Datentyp verfügt über mehrere Darstellungen in nicht verwaltetem Code.  Wenn <xref:System.Runtime.InteropServices.MarshalAsAttribute> nicht angegeben wird, lautet das standardmäßige Marshallingverhalten für den <xref:System.Boolean>\-Datentyp <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>.  Dies ist eine 32\-Bit\-Ganzzahl, die nicht in jedem Fall geeignet ist.  Die für die nicht verwaltete Methode erforderliche boolesche Darstellung sollte ermittelt werden und mit dem entsprechenden <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName> übereinstimmen.  UnmanagedType.Bool ist der Win32\-BOOL\-Typ, der immer 4 Bytes aufweist.  UnmanagedType.U1 sollte für `bool` in C\+\+ oder für andere 1\-Byte\-Typen verwendet werden.  Weitere Informationen finden Sie unter [Default Marshaling for Boolean Types](http://msdn.microsoft.com/de-de/d4c00537-70f7-4ca6-8197-bfc1ec037ff9).  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, wenden Sie <xref:System.Runtime.InteropServices.MarshalAsAttribute> auf den <xref:System.Boolean>\-Parameter oder \-Rückgabewert an.  Legen Sie den Wert des Attributs auf den entsprechenden <xref:System.Runtime.InteropServices.UnmanagedType> fest.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  Auch wenn das standardmäßige Marshallingverhalten geeignet ist, lässt sich der Code sehr viel problemloser verwalten, wenn das Verhalten explizit angegeben wird.  
  
## Beispiel  
 Im folgenden Beispiel werden zwei Plattformaufrufmethoden veranschaulicht, die mit den entsprechenden <xref:System.Runtime.InteropServices.MarshalAsAttribute>\-Attributen markiert sind.  
  
 [!code-cs[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CSharp/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cs)]
 [!code-vb[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/VisualBasic/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.vb)]
 [!code-cpp[FxCop.Interoperability.BoolMarshalAs#1](../code-quality/codesnippet/CPP/ca1414-mark-boolean-p-invoke-arguments-with-marshalas_1.cpp)]  
  
## Verwandte Regeln  
 [CA1901: Deklarationen von P\/Invoke müssen portabel sein](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)  
  
 [CA2101: Marshalling für P\/Invoke\-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
## Siehe auch  
 <xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=fullName>   
 [Default Marshaling for Boolean Types](http://msdn.microsoft.com/de-de/d4c00537-70f7-4ca6-8197-bfc1ec037ff9)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)