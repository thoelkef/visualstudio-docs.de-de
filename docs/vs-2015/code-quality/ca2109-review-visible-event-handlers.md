---
title: 'CA2109: Sichtbare Ereignishandler überprüfen | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2109
- ReviewVisibleEventHandlers
helpviewer_keywords:
- ReviewVisibleEventHandlers
- CA2109
ms.assetid: 8f8fa0ee-e94e-400e-b516-24d8727725d7
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 3ddcab6e0f416837bcd7b01521a6d77ddce691b9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520977"
---
# <a name="ca2109-review-visible-event-handlers"></a>CA2109: Sichtbare Ereignishandler überprüfen.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Element|Wert|
|-|-|
|TypName|ReviewVisibleEventHandlers|
|CheckId|CA2109|
|Category|Microsoft.Security|
|Unterbrechende Änderung|Breaking|

## <a name="cause"></a>Ursache
 Eine öffentliche oder geschützte Ereignisbehandlungsmethode wurde erkannt.

## <a name="rule-description"></a>Beschreibung der Regel
 Eine extern sichtbare Ereignis Behandlungsmethode stellt ein Sicherheitsproblem dar, das überprüft werden muss.

 Ereignisbehandlungsmethoden sollten nur dann verfügbar gemacht werden, wenn dies absolut notwendig ist. Ein Ereignishandler, ein Delegattyp, der die verfügbar gemachte Methode aufruft, kann beliebigen Ereignissen hinzugefügt werden, solange der Handler und die Ereignis Signaturen einander entsprechen. Ereignisse können potenziell von beliebigem Code ausgelöst werden und werden häufig durch hochgradig vertrauenswürdigen Systemcode als Reaktion auf Benutzeraktionen wie das Klicken auf eine Schaltfläche ausgelöst. Durch das Hinzufügen einer Sicherheitsüberprüfung zu einer Ereignis Behandlungsmethode wird nicht verhindert, dass Code einen Ereignishandler registriert, der die-Methode aufruft.

 Eine Anforderung kann eine Methode, die von einem Ereignishandler aufgerufen wird, nicht zuverlässig schützen. Sicherheitsanforderungen helfen dabei, Code vor nicht vertrauenswürdigen Aufrufern zu schützen, indem die Aufrufer in der Aufruf Listen Code, der einem Ereignis einen Ereignishandler hinzufügt, ist nicht notwendigerweise in der aufrufsstapel vorhanden, wenn die Methoden des Ereignis Handlers ausgeführt werden. Daher verfügt die Aufruf Listen möglicherweise nur über hochgradig vertrauenswürdige Aufrufer, wenn die Ereignishandlermethode aufgerufen wird. Dies bewirkt, dass die von der Ereignishandlermethode gemachten Anforderungen erfolgreich sind. Außerdem kann die angeforderte Berechtigung bestätigt werden, wenn die-Methode aufgerufen wird. Aus diesen Gründen kann das Risiko, dass ein Verstoß gegen diese Regel nicht behoben werden kann, nur nach dem Überprüfen der Ereignis Behandlungsmethode bewertet werden. Wenn Sie den Code überprüfen, berücksichtigen Sie die folgenden Probleme:

- Führt der Ereignishandler Vorgänge aus, die gefährlich oder ausnutzbar sind, z. b. das Erteilen von Berechtigungen oder das Unterdrücken der Berechtigung für nicht verwalteten Code?

- Was sind die Sicherheitsbedrohungen für und aus Ihrem Code, da Sie jederzeit mit nur sehr vertrauenswürdigen Aufrufern im Stapel ausgeführt werden können?

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Um einen Verstoß gegen diese Regel zu beheben, überprüfen Sie die-Methode, und bewerten Sie Folgendes:

- Können Sie die Ereignis Behandlungsmethode nicht öffentlich machen?

- Können Sie alle gefährlichen Funktionen aus dem Ereignishandler verschieben?

- Wenn ein Sicherheitsbedarf besteht, kann dies auf andere Weise erreicht werden?

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Unterdrücken Sie eine Warnung aus dieser Regel nur nach einer sorgfältigen Sicherheitsüberprüfung, um sicherzustellen, dass Ihr Code keine Sicherheitsbedrohung darstellt.

## <a name="example"></a>Beispiel
 Der folgende Code zeigt eine Ereignis Behandlungsmethode, die von schädlichem Code missbraucht werden kann.

 [!code-csharp[FxCop.Security.EventSecLib#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.EventSecLib/cs/FxCop.Security.EventSecLib.cs#1)]

## <a name="see-also"></a>Weitere Informationen
 <xref:System.Security.CodeAccessPermission.Demand%2A?displayProperty=fullName> <xref:System.EventArgs?displayProperty=fullName>
 [Sicherheitsforderungen](https://msdn.microsoft.com/324c14f8-54ff-494d-9fd1-bfd20962c8ba)
