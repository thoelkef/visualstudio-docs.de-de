---
title: 'CA2103: Imperative Sicherheit überprüfen | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- CA2103
- ReviewImperativeSecurity
helpviewer_keywords:
- CA2103
- ReviewImperativeSecurity
ms.assetid: d24fde71-bdf6-46c0-8965-9a73dc33c1aa
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f5a46629efacc37af593e4cd7487b69031cf6bb1
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/16/2018
---
# <a name="ca2103-review-imperative-security"></a>CA2103: Imperative Sicherheit überprüfen
|||  
|-|-|  
|TypeName|ReviewImperativeSecurity|  
|CheckId|CA2103|  
|Kategorie|Microsoft.Security|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Eine Methode verwendet imperative Sicherheit und erstellt möglicherweise die Berechtigung mit Zustandsinformationen oder Rückgabewerten, die sich ändern können, während die Forderung wirksam ist.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Imperativer Sicherheit verwendet verwaltete Objekte angeben, Berechtigungen und Sicherheitsaktionen während der Ausführung von Code, die im Vergleich zu deklarative Sicherheit, der Attribute verwendet wird, um Berechtigungen und Aktionen in den Metadaten speichern. Imperativer Sicherheit ist sehr flexibel, da können Sie legen Sie den Status des ein Berechtigungsobjekt und Auswählen von Sicherheitsaktionen mithilfe von Informationen, die erst zur Laufzeit nicht verfügbar ist. Zusammen, die mit stammen Flexibilität das Risiko, das die Laufzeitinformationen, die Sie verwenden, um zu bestimmen, dass der Status einer Berechtigung nicht bleibt unverändert, solange die Aktion aktiviert ist.  
  
 Verwenden Sie, wenn irgend möglich, deklarative Sicherheit. Deklarative Befehle sind einfacher zu verstehen.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Überprüfen Sie die Anforderungen imperative Sicherheit, um sicherzustellen, dass der Zustand der Berechtigung nicht von den Informationen abhängig wird, die sich ändern können, solange die Berechtigung verwendet wird.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Sie können ruhig zum Unterdrücken einer Warnung dieser Regel, wenn die Berechtigung nicht zum Ändern von Daten. Allerdings ist es besser, die imperative Forderung in die entsprechende deklarative zu ändern.  
  
## <a name="see-also"></a>Siehe auch  
 [Schreiben von sicherem Richtlinien](/dotnet/standard/security/secure-coding-guidelines)   
 [Daten und Modellierung](/dotnet/framework/data/index)