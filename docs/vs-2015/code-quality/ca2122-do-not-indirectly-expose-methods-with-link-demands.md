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
ms.openlocfilehash: 846ce010cddfd505bb967ec612a5c31dd8321977
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544325"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Methoden mit Linkaufrufen nicht indirekt verfügbar machen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|value|
|-|-|
|TypName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Nicht unterbrechende Änderung|

## <a name="cause"></a>Ursache
 Ein öffentliches oder geschütztes Mitglied hat einen [Link](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) und wird von einem Member aufgerufen, der keine Sicherheitsüberprüfungen ausführt.

## <a name="rule-description"></a>Beschreibung der Regel
 Ein Linkaufruf überprüft nur die Berechtigungen des unmittelbaren Aufrufers. Wenn ein Member `X` keine Sicherheitsanforderungen seiner Aufrufer erfüllt und Code aufruft, der durch einen Link Aufruf geschützt ist, kann ein Aufrufer ohne die erforderliche Berechtigung `X` für den Zugriff auf den geschützten Member verwenden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Fügen Sie dem-Element eine Sicherheits [Daten-und Modellierungs-](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) oder Verknüpfungs Anforderung hinzu, damit kein unsicherer Zugriff mehr auf den Member mit Link Bedarf geschützt wird.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Um eine Warnung aus dieser Regel sicher zu unterdrücken, müssen Sie sicherstellen, dass Ihr Code den Aufrufern nicht den Zugriff auf Vorgänge oder Ressourcen gewährt, die auf zerstörerische Weise verwendet werden können.

## <a name="example"></a>Beispiel
 Die folgenden Beispiele zeigen eine Bibliothek, die gegen die Regel verstößt, und eine Anwendung, die die Schwachstellen der Bibliothek veranschaulicht. Die Beispiel Bibliothek stellt zwei Methoden bereit, die gegen die Regel verstoßen. Die- `EnvironmentSetting` Methode wird durch einen Link Aufruf für den uneingeschränkten Zugriff auf Umgebungsvariablen gesichert. Die- `DomainInformation` Methode stellt keine Sicherheitsanforderungen Ihrer Aufrufer her, bevor Sie aufruft `EnvironmentSetting` .

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Beispiel
 Die folgende Anwendung ruft den nicht geschützten Bibliotheks Member auf.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Folgende Ergebnisse werden zurückgegeben:

 **Wert aus ungesichertem Mitglied: Seattle.Corp.contoso.com**
## <a name="see-also"></a>Weitere Informationen
 Link " [sichere Codierungs Richtlinien](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) " [erfordert](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [Daten und Modellierung](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)
