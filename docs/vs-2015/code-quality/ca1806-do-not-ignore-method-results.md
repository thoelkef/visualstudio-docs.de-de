---
title: 'CA1806: Methodenergebnisse nicht ignorieren | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1806
- DoNotIgnoreMethodResults
helpviewer_keywords:
- CA1806
- DoNotIgnoreMethodResults
ms.assetid: fd805687-0817-481e-804e-b62cfb3b1076
caps.latest.revision: 27
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: c0af1f7270cca341b713c5036b2c457f5964c0bf
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/23/2019
ms.locfileid: "58959681"
---
# <a name="ca1806-do-not-ignore-method-results"></a>CA1806: Methodenergebnisse nicht ignorieren.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotIgnoreMethodResults|  
|CheckId|CA1806|  
|Kategorie|Microsoft.Usage|  
|Unterbrechende Änderung|Nicht unterbrechende Änderung|  
  
## <a name="cause"></a>Ursache  
 Es gibt mehrere mögliche Gründe für diese Warnung aus:  
  
- Ist ein neues Objekt erstellt, aber nie verwendet.  
  
- Eine Methode, die erstellt und gibt eine neue Zeichenfolge aufgerufen wird, und die neue Zeichenfolge wird nie verwendet.  
  
- Eine COM- oder P/Invoke-Methode, die einen HRESULT oder den Fehlercode Code zurückgibt, der nie verwendet wird. Regelbeschreibung  
  
  Unnötige objekterstellung und die zugeordneten Garbagecollection des nicht verwendeten Objekts wird Leistung beeinträchtigt.  
  
  Zeichenfolgen sind unveränderlich, und Methoden, z. B. String.ToUpper gibt eine neue Instanz der eine Zeichenfolge anstatt in der Instanz der Zeichenfolge in der aufrufenden Methode ändern.  
  
  Wird ignoriert. HRESULT oder den Fehlercode kann zu unerwartetem Verhalten in fehlerbedingungen oder Ressourcenmangel Bedingungen führen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Wenn eine-Methode eine neue Instanz der B-Objekt, die nie verwendet wird erstellt, übergeben Sie die Instanz als Argument an eine andere Methode oder weisen Sie die Instanz einer Variablen zu. Wenn die objekterstellung nicht erforderlich ist, entfernt werden die.- oder -  
  
 Wenn die Methode A Methode B aufruft, aber verwendet nicht die neue Zeichenfolgeninstanz, die die B-Methode zurückgibt. Übergeben Sie die Instanz als Argument an eine andere Methode, weisen Sie die Instanz einer Variablen zu. Ein, oder entfernen Sie den Aufruf aus, wenn es nicht erforderlich ist.  
  
 - oder -   
  
 Wenn die Methode A Methode B aufruft, jedoch nicht den HRESULT-Wert verwendet, oder Fehlercode, die zurückgegeben der Methode. Verwenden Sie das Ergebnis in einer bedingungsanweisung, weisen Sie das Ergebnis einer Variablen oder als Argument an eine andere Methode übergeben.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nicht, es sei denn, der Vorgang der Erstellung des Objekts einige Zweck dient.  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Klasse, die das Ergebnis des Aufrufs von String.Trim ignoriert.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults#1](FxCop.Usage.DoNotIgnoreMethodResults#1)]  -->  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem das Ergebnis der String.Trim an die Variable, die, der es aufgerufen wurde.  
  
<!-- TODO: review snippet reference  [!CODE [FxCop.Usage.DoNotIgnoreMethodResults2#1](FxCop.Usage.DoNotIgnoreMethodResults2#1)]  -->  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die kein Objekt, das erstellt wird.  
  
> [!NOTE]
>  Diese Verletzung kann nicht in Visual Basic nicht reproduziert werden.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cpp/FxCop.Usage.DoNotIgnoreMethodResults3.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/cs/FxCop.Usage.DoNotIgnoreMethodResults3.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults3#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults3/vb/FxCop.Usage.DoNotIgnoreMethodResults3.vb#1)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, durch das Entfernen der Erstellung eines Objekts nicht erforderlichen.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cpp/FxCop.Usage.DoNotIgnoreMethodResults4.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/cs/FxCop.Usage.DoNotIgnoreMethodResults4.cs#1)]
 [!code-vb[FxCop.Usage.DoNotIgnoreMethodResults4#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults4/vb/FxCop.Usage.DoNotIgnoreMethodResults4.vb#1)]  
  
## <a name="example"></a>Beispiel  
 Das folgende Beispiel zeigt eine Methode, die den Fehlercode nicht berücksichtigt, den die systemeigene Methode GetShortPathName zurückgibt.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cpp/FxCop.Usage.DoNotIgnoreMethodResults5.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults5#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults5/cs/FxCop.Usage.DoNotIgnoreMethodResults5.cs#1)]  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel wird der vorherige Verstoß korrigiert, indem Sie den Fehlercode und eine Ausnahme auszulösen, wenn der Aufruf fehlschlägt.  
  
 [!code-cpp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cpp/FxCop.Usage.DoNotIgnoreMethodResults6.cpp#1)]
 [!code-csharp[FxCop.Usage.DoNotIgnoreMethodResults6#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.DoNotIgnoreMethodResults6/cs/FxCop.Usage.DoNotIgnoreMethodResults6.cs#1)]