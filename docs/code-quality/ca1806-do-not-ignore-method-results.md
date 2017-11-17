---
title: 'CA1806: Methodenergebnisse nicht ignorieren | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 58da9a40f8cbbf8a506feb35dcba8a8e9f405899
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Methodenergebnisse nicht ignorieren
|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Es gibt mehrere mögliche Ursachen für diese Warnung:  
  
-   Ein neues Objekt wird erstellt, aber nie verwendet.  
  
-   Eine Methode, die eine neue Zeichenfolge erstellt und zurückgibt, wird aufgerufen, und die neue Zeichenfolge wird nie verwendet.  
  
-   Eine COM- oder P/Invoke-Methode, die einen HRESULT oder die Fehler Code zurückgibt, der nie verwendet wird. Regelbeschreibung  
  
 Unnötige objekterstellung und die zugeordneten Garbagecollection des nicht verwendeten Objekts zu Leistungseinbußen.  
  
 Zeichenfolgen sind unveränderlich und Methoden wie z. B. String.ToUpper eine neue Instanz einer Zeichenfolge statt ändern die Instanz der Zeichenfolge in der aufrufenden Methode zurückgibt.  
  
 Ignorieren von HRESULT oder Fehlercode kann unerwartetes Verhalten auftreten von Fehlern oder Ressourcenmangel Bedingungen führen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn die Methode A eine neue Instanz der B-Objekt, die nie verwendet wird erstellt, übergeben Sie die Instanz als Argument an eine andere Methode oder weisen Sie die Instanz einer Variablen zu. Wenn die objekterstellung nicht erforderlich ist, entfernen Sie die darauf- oder -  
  
 Wenn die Methode A Methode B aufruft, jedoch nicht die neue Zeichenfolgeninstanz, die der Methodenrückgabe B verwendet. Übergeben Sie die Instanz als Argument an eine andere Methode, weisen Sie die Instanz einer Variablen zu. Ein, oder entfernen Sie den Aufruf aus, wenn es nicht erforderlich ist.  
  
 - oder -   
  
 Wenn die Methode A Methode B aufruft, aber verwendet nicht das HRESULT oder Fehlercodes, die zurückgegeben der Methode. Das Ergebnis in einer bedingten Anweisung verwenden, das Ergebnis einer Variablen zuweisen oder an eine andere Methode als Argument zu übergeben.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie keine Warnung dieser Regel, es sei denn, beim Erstellen des Objekts einige Zweck dient.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die das Ergebnis des Aufrufs von String.Trim ignoriert.  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_1.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_1.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_1.cpp)]  
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird der vorherige Verstoß durch das erneute Zuordnen des Ergebnisses der String.Trim zurück an die Variable, der es aufgerufen wurde korrigiert.  
  
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_2.cs)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/VisualBasic/ca1806-do-not-ignore-method-results_2.vb)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_2.cpp)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die kein Objekt verwenden, das erstellt wird.  
  
> [!NOTE]
>  Diese Regel kann nicht in Visual Basic reproduziert werden.  

 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_3.cpp)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_3.cs)]   
  
## <a name="example"></a>Beispiel  
 Im folgende Beispiel wird der vorherige Verstoß durch das Entfernen der unnötige Erstellung eines Objekts korrigiert.  

 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CSharp/ca1806-do-not-ignore-method-results_4.cs)]
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../code-quality/codesnippet/CPP/ca1806-do-not-ignore-method-results_4.cpp)] 

<!-- Examples don't exist for the below... -->
<!--
## Example  
 The following example shows a method that ignores the error code that the native method GetShortPathName returns.  
  
## Example  
 The following example fixes the previous violation by checking the error code and throwing an exception when the call fails.  
-->