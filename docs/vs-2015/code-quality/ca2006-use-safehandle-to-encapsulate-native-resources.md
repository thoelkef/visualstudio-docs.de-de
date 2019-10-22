---
title: 'CA2006: SafeHandle verwenden, um native Ressourcen zu Kapseln | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 394fafb0c9185a5e11ba759a5b873236956cf25b
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652212"
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 Verwalteter Code verwendet <xref:System.IntPtr>, um auf native Ressourcen zuzugreifen.

## <a name="rule-description"></a>Regelbeschreibung
 Die Verwendung von `IntPtr` in verwaltetem Code kann auf ein potenzielles Sicherheits-und Zuverlässigkeits Problem hindeuten. Alle Verwendungsmöglichkeiten von `IntPtr` müssen überprüft werden, um zu bestimmen, ob die Verwendung eines <xref:System.Runtime.InteropServices.SafeHandle> oder einer ähnlichen Technologie notwendig ist. Es treten Probleme auf, wenn die `IntPtr` eine systemeigene Ressource (z. b. Arbeitsspeicher, ein Datei Handle oder einen Socket) darstellt, die der verwaltete Code als Besitzer hat. Wenn der verwaltete Code die Ressource besitzt, muss er auch die ihm zugeordneten systemeigenen Ressourcen freigeben, da ein Ausfall nicht zu einer Ressourcen Lecks führen würde.

 In solchen Szenarien bestehen auch Sicherheits-oder Zuverlässigkeitsprobleme, wenn der Multithread-Zugriff auf die `IntPtr` zulässig ist und eine Möglichkeit besteht, die durch die `IntPtr` dargestellte Ressource freizugeben. Diese Probleme umfassen die Wiederverwendung des `IntPtr` Werts in der Ressourcen Freigabe, während die gleichzeitige Verwendung der Ressource auf einem anderen Thread erfolgt. Dies kann Racebedingungen verursachen, bei denen ein Thread Daten lesen oder schreiben kann, die mit der falschen Ressource verknüpft sind. Wenn Ihr Typ z. b. ein Betriebssystem Handle als `IntPtr` speichert und es den Benutzern ermöglicht, sowohl **Close** als auch eine beliebige andere Methode aufzurufen, die dieses Handle gleichzeitig und ohne Synchronisierung verwendet, hat der Code ein Problem beim wieder verwenden.

 Diese Problembehandlung kann zu Daten Beschädigungen und häufig zu einem Sicherheitsrisiko führen. `SafeHandle` und seine gleich geordnete Klasse <xref:System.Runtime.InteropServices.CriticalHandle> bieten einen Mechanismus zum Kapseln eines systemeigenen Handles für eine Ressource, damit solche Threading Probleme vermieden werden können. Darüber hinaus können Sie `SafeHandle` und dessen gleich geordnete Klasse `CriticalHandle` für andere Threading Probleme verwenden, um beispielsweise die Lebensdauer von verwalteten Objekten sorgfältig zu steuern, die eine Kopie des nativen Handles über Aufrufe von systemeigenen Methoden enthalten. In dieser Situation können Sie häufig Aufrufe an `GC.KeepAlive` entfernen. Der Leistungs Aufwand, den Sie bei der Verwendung `SafeHandle` und in geringerem Maße `CriticalHandle`, kann häufig durch einen sorgfältigen Entwurf reduziert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Konvertieren Sie `IntPtr` Verwendung in `SafeHandle`, um den Zugriff auf systemeigene Ressourcen sicher zu verwalten. Beispiele finden Sie im Thema <xref:System.Runtime.InteropServices.SafeHandle> Referenz.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Sie sollten diese Warnung nicht unterdrücken.

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable>
