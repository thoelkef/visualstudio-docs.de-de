---
title: "CA1404: GetLastError unmittelbar nach P/Invoke aufrufen | Microsoft Docs"
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
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
helpviewer_keywords: 
  - "CallGetLastErrorImmediatelyAfterPInvoke"
  - "CA1404"
ms.assetid: 52ae9eff-50f9-4b2f-8039-ca7e49fba88e
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1404: GetLastError unmittelbar nach P/Invoke aufrufen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|CallGetLastErrorImmediatelyAfterPInvoke|  
|CheckId|CA1404|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A?displayProperty=fullName>\-Methode oder die entsprechende `GetLastError`\-Win32\-Funktion wird aufgerufen, und unmittelbar zuvor wird keine Plattformaufrufmethode aufgerufen.  
  
## Regelbeschreibung  
 Eine Plattformaufrufmethode greift auf nicht verwalteten Code zu und wird mit dem `Declare`\-Schlüsselwort in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] oder dem <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName>\-Attribut definiert.  Bei einem Fehler rufen nicht verwaltete Funktionen im Allgemeinen die `SetLastError`\-Win32\-Funktion auf, um einen Fehlercode festzulegen, der dem Fehler zugeordnet wird.  Der Aufrufer der fehlgeschlagenen Funktion ruft die `GetLastError`\-Win32\-Funktion auf, um den Fehlercode abzurufen und die Ursache des Fehlers zu ermitteln.  Der Fehlercode wird threadweise verwaltet und durch den nächsten Aufruf von `SetLastError` überschrieben.  Nach einem Aufruf einer fehlgeschlagenen Plattformaufrufmethode kann der Fehlercode durch verwalteten Code abgerufen werden. Dazu wird die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>\-Methode aufgerufen.  Da der Fehlercode durch interne Aufrufe überschrieben werden kann, die von anderen verwalteten Klassenbibliotheksmethoden stammen, sollte die `GetLastError`\-Methode oder die <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>\-Methode unmittelbar nach dem Aufruf der Plattformaufrufmethode aufgerufen werden.  
  
 Die Regel ignoriert Aufrufe der folgenden verwalteten Member, wenn diese zwischen dem Aufruf der Plattformaufrufmethode und dem Aufruf von <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A> erfolgen.  Diese Member ändern den Fehlercode nicht, und mithilfe dieser Member lässt sich feststellen, ob bestimmte Aufrufe von Plattformaufruftmethoden erfolgreich waren.  
  
-   <xref:System.IntPtr.Zero?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Equality%2A?displayProperty=fullName>  
  
-   <xref:System.IntPtr.op_Inequality%2A?displayProperty=fullName>  
  
-   <xref:System.Runtime.InteropServices.SafeHandle.IsInvalid%2A?displayProperty=fullName>  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, verschieben Sie den Aufruf in <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>, damit er unmittelbar auf den Aufruf der Plattformaufrufmethode folgt.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn der Code zwischen dem Aufruf der Plattformaufrufmethode und dem Aufruf der <xref:System.Runtime.InteropServices.Marshal.GetLastWin32Error%2A>\-Methode keine explizite oder implizite Änderung des Fehlercodes bewirken kann.  
  
## Beispiel  
 Das folgende Beispiel zeigt eine Methode, die gegen die Regel verstößt, und eine Methode, die der Regel entspricht.  
  
 [!code-vb[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/VisualBasic/ca1404-call-getlasterror-immediately-after-p-invoke_1.vb)]
 [!code-cs[FxCop.Interoperability.LastErrorPInvoke#1](../code-quality/codesnippet/CSharp/ca1404-call-getlasterror-immediately-after-p-invoke_1.cs)]  
  
## Verwandte Regeln  
 [CA1060: P\/Invokes in NativeMethods\-Klasse verschieben](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)  
  
 [CA1400: Für P\/Invoke müssen Einstiegspunkte vorhanden sein](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)  
  
 [CA1401: P\/Invokes dürfen nicht sichtbar sein](../code-quality/ca1401-p-invokes-should-not-be-visible.md)  
  
 [CA2101: Marshalling für P\/Invoke\-Zeichenfolgenargumente festlegen](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)  
  
 [CA2205: Verwaltete Entsprechungen der Win32 API verwenden](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)