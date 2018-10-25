---
title: 'CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
helpviewer_keywords:
- CA2220
- FinalizersShouldCallBaseClassFinalizer
ms.assetid: 48329f42-170d-45ee-a381-e33f55a240c5
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 3e00419ed7f6b4d388b9fb28f56d85990a4257b1
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49862709"
---
# <a name="ca2220-finalizers-should-call-base-class-finalizer"></a>CA2220: Finalizer sollten Basisklassen-Finalizer aufrufen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|FinalizersShouldCallBaseClassFinalizer|
|CheckId|CA2220|
|Kategorie|Microsoft.Usage|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein Typ, überschreibt <xref:System.Object.Finalize%2A?displayProperty=fullName> ruft nicht die <xref:System.Object.Finalize%2A> -Methode in der Basisklasse.

## <a name="rule-description"></a>Regelbeschreibung
 Der Abschluss muss durch die Vererbungshierarchie weitergegeben werden. Um dies zu gewährleisten, müssen Typen ihrer Basisklasse aufrufen <xref:System.Object.Finalize%2A> innerhalb ihrer eigenen <xref:System.Object.Finalize%2A> Methode. Den Aufruf von den Basisklassen-Finalizer wird von der C#-Compiler automatisch hinzugefügt.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, rufen Sie des Basistyps <xref:System.Object.Finalize%2A> aus Ihrem <xref:System.Object.Finalize%2A> Methode.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie keine Warnung dieser Regel. Einige Compiler, die die common Language Runtime als Ziel legen Sie einen Aufruf der Basistyp des Finalizers in die Microsoft intermediate Language (MSIL). Wenn eine Warnung dieser Regel gemeldet wird, wird der Compiler kein Aufruf eingefügt, und müssen Sie es an Ihrem Code hinzufügen.

## <a name="example"></a>Beispiel
 Das folgende Visual Basic-Beispiel zeigt ein `TypeB` ordnungsgemäß aufruft, die <xref:System.Object.Finalize%2A> -Methode in der Basisklasse.

 [!code-vb[FxCop.Usage.IDisposableBaseCalled#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.IDisposableBaseCalled/vb/FxCop.Usage.IDisposableBaseCalled.vb#1)]

## <a name="see-also"></a>Siehe auch
 [Dispose-Muster](http://msdn.microsoft.com/library/31a6c13b-d6a2-492b-9a9f-e5238c983bcb)



