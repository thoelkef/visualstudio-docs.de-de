---
title: "CA1901: Deklarationen von P/Invoke m&#252;ssen portabel sein | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
helpviewer_keywords: 
  - "CA1901"
  - "PInvokeDeclarationsShouldBePortable"
ms.assetid: 90361812-55ca-47f7-bce9-b8775d3b8803
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1901: Deklarationen von P/Invoke m&#252;ssen portabel sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PInvokeDeclarationsShouldBePortable|  
|CheckId|CA1901|  
|Kategorie \(Category\)|Microsoft.Portability|  
|Unterbrechende Änderung|Unterbrechend – Wenn das P\/Invoke außerhalb der Assembly sichtbar ist.  Nicht unterbrechend – Wenn P\/Invoke nicht außerhalb der Assembly sichtbar ist.|  
  
## Ursache  
 Diese Regel wertet die Größe der einzelnen Parameter und den Rückgabewert einer P\/Invoke\-Deklaration aus und überprüft, ob die zugehörige Größe beim Marshallen an nicht verwalteten Code auf einer 32\-Bit\- oder 64\-Bit\-Plattform richtig ist.  Der am häufigsten auftretende Verstoß gegen diese Regel ist die Übergabe einer ganz Zahl fester Größe, wenn eine plattformabhängige Variable in Zeigergröße erforderlich ist.  
  
## Regelbeschreibung  
 Wenn eines der folgenden Szenarien gegen die Regel verstößt, tritt diese Regel auf:  
  
-   Der Rückgabewert oder Parametertyp wurde als Ganzzahl fester Größe anstatt als `IntPtr` typisiert.  
  
-   Der Rückgabewert oder Parametertyp wurde als `IntPtr` anstatt als Ganzzahl fester Größe typisiert.  
  
## Behandeln von Verstößen  
 Sie können diesen Verstoß beheben, indem Sie statt mit `Int32` oder `UInt32` mithilfe von `IntPtr` oder `UIntPtr` Handles darstellen.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Diese Warnung sollte nicht unterdrückt werden.  
  
## Beispiel  
 Im folgenden Beispiel wird ein Verstoß gegen diese Regel veranschaulicht.  
  
```c#  
internal class NativeMethods  
{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]  
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, IntPtr nIconIndex);  
}  
```  
  
 In diesem Beispiel wird der `nIconIndex`\-Parameter als `IntPtr` deklariert, der 4 Bytes hat auf einer 32\-Bit\-Plattform und 8 Bytes hat auf einer 64\-Bit\-Plattform ist.  In der nicht verwaltetem Deklaration, die erfolgreich ist, sehen, dass `nIconIndex` eine ganze Zahl ohne Vorzeichen auf allen Plattformen ist.  
  
```c#  
HICON ExtractIcon(HINSTANCE hInst, LPCTSTR lpszExeFileName,   
    UINT nIconIndex);  
```  
  
## Beispiel  
 Um den Verstoß zu beheben, ändern Sie die Deklaration wie folgt:  
  
```c#  
internal class NativeMethods{  
    [DllImport("shell32.dll", CharSet=CharSet.Auto)]   
    internal static extern IntPtr ExtractIcon(IntPtr hInst,   
        string lpszExeFileName, uint nIconIndex);  
}  
```  
  
## Siehe auch  
 [Portabilitätswarnungen](../code-quality/portability-warnings.md)