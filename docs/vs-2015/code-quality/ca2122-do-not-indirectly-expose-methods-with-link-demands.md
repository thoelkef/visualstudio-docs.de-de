---
title: 'CA2122: Methoden mit Link aufrufen nicht indirekt verfügbar machen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 099e5f3f9a09eef57ce1b888601f61e85ceb97c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643402"
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
 Ein öffentliches oder geschütztes Mitglied hat einen [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) und wird von einem Member aufgerufen, der keine Sicherheitsüberprüfungen ausführt.

## <a name="rule-description"></a>Regelbeschreibung
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. Wenn ein Element `X` keine Sicherheitsanforderungen seiner Aufrufer erfüllt und Code aufruft, der durch einen Link Aufruf geschützt ist, kann ein Aufrufer ohne die erforderliche Berechtigung `X` verwenden, um auf den geschützten Member zuzugreifen.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie dem-Element eine Sicherheits [Daten-und Modellierungs-](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oder Verknüpfungs Anforderung hinzu, damit kein unsicherer Zugriff mehr auf den Member mit Link Bedarf geschützt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code den Aufrufern nicht den Zugriff auf Vorgänge oder Ressourcen gewährt, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele zeigen eine Bibliothek, die gegen die Regel verstößt, und eine Anwendung, die die Schwachstellen der Bibliothek veranschaulicht. Die Beispiel Bibliothek stellt zwei Methoden bereit, die gegen die Regel verstoßen. Die `EnvironmentSetting`-Methode wird durch einen Link Aufruf für den uneingeschränkten Zugriff auf Umgebungsvariablen gesichert. Die `DomainInformation`-Methode führt keine Sicherheitsanforderungen Ihrer Aufrufer vor dem Aufrufen von `EnvironmentSetting`.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft den nicht geschützten Bibliotheks Member auf.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Wert aus ungesichertem Mitglied: Seattle.Corp.contoso.com**
## <a name="see-also"></a>Siehe auch
 Link " [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) " [erfordert](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
