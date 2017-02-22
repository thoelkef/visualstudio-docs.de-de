---
title: "CA1060: P/Invokes in NativeMethods-Klasse verschieben | Microsoft Docs"
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
  - "MovePInvokesToNativeMethodsClass"
  - "CA1060"
helpviewer_keywords: 
  - "CA1060"
  - "MovePInvokesToNativeMethodsClass"
ms.assetid: 06686c8c-6ad3-42f7-a355-cbaefa347cfc
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1060: P/Invokes in NativeMethods-Klasse verschieben
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MovePInvokesToNativeMethodsClass|  
|CheckId|CA1060|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Eine Methode verwendet Plattformaufrufdienste für den Zugriff auf nicht verwalteten Code und ist kein Member einer der **NativeMethods**\-Klassen.  
  
## Regelbeschreibung  
 Plattformaufrufmethoden, z. B. solche, die mit dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>\-Attribut gekennzeichnet sind, oder Methoden, die in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] mithilfe des `Declare`\-Schlüsselworts definiert wurden, greifen auf nicht verwalteten Code zu.  Diese Methoden müssen in einer der folgenden Klassen enthalten sein:  
  
-   **NativeMethods** – Diese Klasse unterdrückt keine Stackwalks für eine Berechtigung für nicht verwalteten Code. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> darf auf diese Klasse nicht angewendet werden.\) Diese Klasse ist für Methoden vorgesehen, die an einer beliebigen Stelle verwendet werden können, da ein Stackwalk ausgeführt wird.  
  
-   **SafeNativeMethods** – Diese Klasse unterdrückt Stackwalks für eine Berechtigung für nicht verwalteten Code. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> wird auf diese Klasse angewendet.\) Diese Klasse ist für Methoden vorgesehen, die von jedem Benutzer gefahrlos aufgerufen werden können.  Aufrufer dieser Methoden müssen keine vollständige Sicherheitsüberprüfung durchführen, um sicherzustellen, dass ihre Verwendung sicher ist, da die Methoden für jeden Aufrufer kein Risiko darstellen.  
  
-   **UnsafeNativeMethods** – Diese Klasse unterdrückt Stackwalks für eine Berechtigung für nicht verwalteten Code. \(<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute?displayProperty=fullName> wird auf diese Klasse angewendet.\) Diese Klasse ist für Methoden vorgesehen, die möglicherweise ein Sicherheitsrisiko darstellen.  Jeder Aufrufer dieser Methoden muss eine vollständige Sicherheitsüberprüfung durchführen, um sicherzustellen, dass die Verwendung sicher ist, da kein Stackwalk ausgeführt wird.  
  
 Diese Klassen sind als `internal` \(`Friend` in Visual Basic\) deklariert und deklarieren einen privaten Konstruktor, um die Erstellung neuer Instanzen zu verhindern.  Die Methoden in diesen Klassen sollten `static` und `internal` \(`Shared` und `Friend` in Visual Basic\) sein.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu korrigieren, verschieben Sie die Methode in die entsprechende **NativeMethods**\-Klasse.  Für die meisten Anwendungen reicht es aus, P\/Invokes in eine neue Klasse mit dem Namen **NativeMethods** zu verschieben.  
  
 Wenn Sie jedoch Bibliotheken entwickeln, die in anderen Anwendungen verwendet werden sollen, sollten Sie zwei weitere Klassen mit dem Namen **SafeNativeMethods** und **UnsafeNativeMethods** definieren.  Diese Klassen ähneln der **NativeMethods**\-Klasse, werden jedoch mit einem bestimmten Attribut namens **SuppressUnmanagedCodeSecurityAttribute** markiert.  Wenn dieses Attribut angewendet wird, führt die Laufzeit keinen vollständigen Stackwalk aus, um sicherzustellen, dass alle Aufrufer über die **UnmanagedCode**\-Berechtigung verfügen.  Die Laufzeit überprüft diese Berechtigung normalerweise beim Start.  Da die Überprüfung nicht ausgeführt wird, kann die Leistung bei Aufrufen dieser nicht verwalteten Methoden beträchtlich gesteigert werden und Code mit eingeschränkten Berechtigungen kann darüber hinaus diese Methoden aufrufen.  
  
 Sie sollten jedoch dieses Attribut mit großer Sorgfalt verwenden.  Dies kann bei einer falschen Implementierung ernste Auswirkungen auf die Sicherheit haben.  
  
 Weitere Informationen zum Implementieren der Methoden finden Sie in den Beispielen **NativeMethods**, **SafeNativeMethods** und **UnsafeNativeMethods**.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel.  
  
## Beispiel  
 Im folgenden Beispiel wird eine Methode deklariert, die gegen diese Regel verstößt.  Um den Verstoß zu beheben, sollte **RemoveDirectory** P\/Invoke in die entsprechende Klasse verschoben werden, die nur für die Aufnahme von P\/Invokes vorgesehen ist.  
  
 [!code-vb[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_1.vb)]
 [!code-cs[FxCop.Design.DllImportNativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_1.cs)]  
  
## NativeMethods\-Beispiel  
  
### **Beschreibung**  
 Da die **NativeMethods**\-Klasse nicht mit **SuppressUnmanagedCodeSecurityAttribute** markiert werden sollte, erfordern darin platzierte P\/Invokes die **UnmanagedCode**\-Berechtigung.  Da die meisten Anwendungen vom lokalen Computer ausgeführt werden und zusammen voll vertrauenswürdig sind, stellt dies normalerweise kein Problem dar.  Wenn Sie jedoch wiederverwendbare Bibliotheken entwickeln, sollten Sie erwägen, eine **SafeNativeMethods**\-Klasse oder **UnsafeNativeMethods**\-Klasse zu definieren.  
  
 Im folgenden Beispiel wird eine **Interaction.Beep**\-Methode veranschaulicht, die die **MessageBeep**\-Funktion von user32.dll umschließt.  Der P\/Invoke **MessageBeep** wird in der **NativeMethods**\-Klasse platziert.  
  
### Code  
 [!code-cs[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_2.cs)]
 [!code-vb[FxCop.Design.NativeMethods#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_2.vb)]  
  
## SafeNativeMethods\-Beispiel  
  
### **Beschreibung**  
 P\/Invoke\-Methoden, die für beliebige Anwendungen verfügbar gemacht werden können und keine Nebeneffekte haben, sollten in der Klasse **SafeNativeMethods** platziert werden.  Sie müssen in diesem Fall keine Berechtigungen fordern und nicht besonders darauf achten, von wo sie aufgerufen werden.  
  
 Im folgenden Beispiel wird eine **Environment.TickCount**\-Eigenschaft veranschaulicht, die die **GetTickCount**\-Funktion aus kernel32.dll umschließt.  
  
### Code  
 [!code-vb[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_3.vb)]
 [!code-cs[FxCop.Design.NativeMethodsSafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_3.cs)]  
  
## UnsafeNativeMethods\-Beispiel  
  
### **Beschreibung**  
 P\/Invoke\-Methoden, die nicht sicher aufgerufen werden können und unter Umständen Nebeneffekte verursachen, sollten in einer Klasse mit dem Namen **UnsafeNativeMethods** definiert werden.  Diese Methoden sollten streng überprüft werden, um sicherzustellen, dass sie nicht unbeabsichtigt für den Benutzer verfügbar gemacht werden.  Die Regel [CA2118: Überprüfen der Verwendung von SuppressUnmanagedCodeSecurityAttribute](../code-quality/ca2118-review-suppressunmanagedcodesecurityattribute-usage.md) kann dabei hilfreich sein.  Alternativ sollten die Methoden über eine andere Berechtigung verfügen, die anstelle von **UnmanagedCode** gefordert wird, wenn sie verwendet wird.  
  
 Im folgenden Beispiel wird eine **Cursor.Hide**\-Methode veranschaulicht, die die **ShowCursor**\-Funktion aus user32.dll umschließt.  
  
### Code  
 [!code-vb[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/VisualBasic/ca1060-move-p-invokes-to-nativemethods-class_4.vb)]
 [!code-cs[FxCop.Design.NativeMethodsUnsafe#1](../code-quality/codesnippet/CSharp/ca1060-move-p-invokes-to-nativemethods-class_4.cs)]  
  
## Siehe auch  
 [Entwurfswarnungen](../code-quality/design-warnings.md)