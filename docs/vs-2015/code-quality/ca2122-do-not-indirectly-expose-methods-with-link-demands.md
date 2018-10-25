---
title: 'CA2122: Machen Methoden mit Linkaufrufen nicht indirekt | Microsoft-Dokumentation'
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
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 563805fdd8ba8c30e9fb241cc24136ad0c9e9e06
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912837"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategorie|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentlicher oder geschützter Member wurde ein [Verknüpfungsaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) und wird aufgerufen, indem Sie ein Element, das keine sicherheitsüberprüfungen ausführt.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. Wenn ein Member `X` macht keine sicherheitsanforderungen der Aufrufer Code geschützt durch einen Linkaufruf, einen Aufrufer ohne die erforderliche Berechtigung verwenden, kann Aufrufe `X` auf den geschützten Member zuzugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie einen [Daten und Modellierung](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oder bei Bedarf in das Element verknüpfen, sodass es nicht mehr ungesicherten Zugriff auf den Link bei Bedarf geschützte Member bereitstellt.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um problemlos eine Warnung dieser Regel zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code seinen Aufrufern keinen Zugriff auf Vorgänge oder Ressourcen, die auf schädigende Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele zeigen eine Bibliothek, die gegen die Regel verstößt und eine Anwendung, die die Bibliothek aufzeigt. Die Beispielbibliothek bietet zwei Methoden, die zusammen die Regel verletzen. Die `EnvironmentSetting` Methode wird durch einen Linkaufruf für einen uneingeschränkten Zugriff auf Umgebungsvariablen geschützt. Die `DomainInformation` Methode macht keine sicherheitsanforderungen Aufrufer vor `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft die ungeschützten Bibliothekmembers.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Wert von unsicheren Member: "Seattle.corp.contoso.com"**
## <a name="see-also"></a>Siehe auch
 [Sichern Sie die Richtlinien für das Codieren](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [Linkaufrufe](http://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](http://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)



