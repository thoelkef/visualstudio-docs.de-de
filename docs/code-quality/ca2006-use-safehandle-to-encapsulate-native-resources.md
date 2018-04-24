---
title: 'CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln'
ms.date: 11/04/2016
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2006
- UseSafeHandleToEncapsulateNativeResources
helpviewer_keywords:
- UseSafeHandleToEncapsulateNativeResources
- CA2006
ms.assetid: a71950bd-bcc1-463d-b1f2-5233bc451456
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- cplusplus
ms.openlocfilehash: dc059f606da3229351e749a4e27ad87f2055fa8c
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/19/2018
---
# <a name="ca2006-use-safehandle-to-encapsulate-native-resources"></a>CA2006: SafeHandle verwenden, um systemeigene Ressourcen zu kapseln
|||
|-|-|
|TypeName|UseSafeHandleToEncapsulateNativeResources|
|CheckId|CA2006|
|Kategorie|Microsoft.Reliability|
|Unterbrechende Änderung|Nicht unterbrechend|

## <a name="cause"></a>Ursache
 In verwaltetem Code wird verwendet <xref:System.IntPtr> Zugriff auf systemeigene Ressourcen.

## <a name="rule-description"></a>Regelbeschreibung
 Verwenden von `IntPtr` in verwaltetem Code ein potenzielles Sicherheitsrisiko und Zuverlässigkeitsproblem Problem anzugeben. Alle Vorkommen von `IntPtr` muss überprüft werden, um zu bestimmen, ob die Verwendung von einem <xref:System.Runtime.InteropServices.SafeHandle> , oder eine ähnliche Technologie an seiner Stelle erforderlich ist. Probleme tritt auf, wenn die `IntPtr` stellt eine systemeigene Ressource, z. B. Arbeitsspeicher, ein Dateihandle oder einen Socket, dass der verwaltete Code als Besitzer berücksichtigt wird. Wenn der verwaltete Code die Ressource besitzt, müssen sie auch die systemeigenen Ressourcen zugeordnet, freigeben, da einen Fehler zu diesem Zweck Ressourcenverluste verursachen würde.

 In solchen Szenarien Sicherheit oder Zuverlässigkeit Probleme ist auch vorhanden, wenn multithreaded-Zugriff, um zugelassen wird die `IntPtr` und eine Methode zum Freigeben der Ressource, die durch dargestellt wird die `IntPtr` bereitgestellt wird. Diese Probleme betreffen, wird die Wiederverwendung von der `IntPtr` Wert auf die Ressourcenfreigabe während der gleichzeitigen Verwendung der Ressource auf einem anderen Thread bereitgestellt werden. Dies kann Racebedingungen verursachen, wobei ein Thread Lese- oder Schreibzugriff auf Daten, die die falschen Ressource zugeordnet ist. Wenn der Typ ein Betriebssystemhandle als speichert z. B. ein `IntPtr` und ermöglicht es Benutzern, die beide rufen **schließen** und jede andere Methode, die dieses Handle gleichzeitig und ohne eine Art der Synchronisierung verwendet werden, der Code hat eine Wiederverwendung Handle Problem.

 Dieses Handle, das recycling Problem kann dazu führen, dass beschädigte Daten und in vielen Fällen ein Sicherheitsrisiko. `SafeHandle` und seine nebengeordnete Klasse <xref:System.Runtime.InteropServices.CriticalHandle> bieten einen Mechanismus, um eine systemeigene Handle auf eine Ressource zu kapseln, damit solche Threadingprobleme vermieden werden können. Darüber hinaus können Sie `SafeHandle` und seine nebengeordnete Klasse `CriticalHandle` für andere Threadingprobleme, z. B. die Lebensdauer von verwalteten Objekten sorgfältig zu steuern, die eine Kopie des das systemeigene Handle über Aufrufe von systemeigenen Methoden enthalten. In diesem Fall kann häufig beseitigt werden Aufrufe von `GC.KeepAlive`. Die Leistung Verwaltungsaufwand konfiguriert fallen an, wenn Sie verwenden `SafeHandle` und in einem geringeren Ausmaß `CriticalHandle`, kann häufig durch einen sorgfältigen Entwurf reduziert werden.

## <a name="how-to-fix-violations"></a>Behandeln von Verstößen
 Konvertieren von `IntPtr` mit `SafeHandle` , Zugriff auf systemeigene Ressourcen sicher zu verwalten. Finden Sie unter der <xref:System.Runtime.InteropServices.SafeHandle> Referenzthema Beispiele.

## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?
 Diese Warnung sollte nicht unterdrückt werden.

## <a name="see-also"></a>Siehe auch
 <xref:System.IDisposable>