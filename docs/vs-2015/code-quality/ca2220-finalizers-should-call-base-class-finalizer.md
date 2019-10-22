---
title: 'CA2220: Finalizer sollten Basisklassen-Finalizer abrufen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 1a4538c66d351956da8168d4f84c1895190ab453
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663587"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft. Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, der <xref:System.Object.Finalize%2A?displayProperty=fullName> überschreibt, ruft die <xref:System.Object.Finalize%2A>-Methode nicht in der Basisklasse auf.

## <a name="rule-description"></a>Regelbeschreibung
 Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu gewährleisten, müssen Typen ihre Basisklasse <xref:System.Object.Finalize%2A> Methode aus ihrer eigenen <xref:System.Object.Finalize%2A> Methode abrufen. Der C# Compiler fügt den-Befehl dem Basisklassen-Finalizer automatisch hinzu.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, müssen Sie die <xref:System.Object.Finalize%2A>-Methode des Basistyps von ihrer <xref:System.Object.Finalize%2A>-Methode aus abrufen.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Einige Compiler, die auf abzielen, Common Language Runtime einen-Befehl an den Finalizer des Basistyps in die Microsoft Intermediate Language (MSIL) einfügen. Wenn eine Warnung aus dieser Regel gemeldet wird, fügt der Compiler den-Befehl nicht ein, und Sie müssen ihn dem Code hinzufügen.

## <a name="example"></a>Beispiel
 Im folgenden Visual Basic Beispiel wird ein Typ `TypeB` gezeigt, der die <xref:System.Object.Finalize%2A>-Methode ordnungsgemäß in der-Basisklasse aufruft.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Dispose-Muster](https://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)
