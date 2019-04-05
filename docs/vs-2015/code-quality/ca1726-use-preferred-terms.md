---
title: 'CA1726: Bevorzugte Begriffe verwenden | Microsoft-Dokumentation'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords:
- UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: e31c459d2d5ce8dc114605716c09f8360eca23d3
ms.sourcegitcommit: 3201da3499051768ab59f492699a9049cbc5c3c6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/22/2019
ms.locfileid: "59001844"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation zu Visual Studio finden Sie unter [CA1726: Bevorzugte Begriffe verwenden](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) auf docs.microsoft.com.  
  
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Wichtige – Wenn ausgelöst von Assemblys<br /><br /> Nicht unterbrechend – Wenn ausgelöst von Typparametern|  
  
## <a name="cause"></a>Ursache  
 Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Alternativ enthält den Namen den Begriff Flag oder Flags.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel analysiert einen Bezeichner in Token. Jedes einzelne Token und jeder Kombination aus zwei zusammenhängende token wird mit Begriffen verglichen, die in der Regel und im Abschnitt "veraltet" des benutzerdefinierten Wörterbüchern erstellt werden. Die folgende Tabelle zeigt die Bedingungen, die in der Regel, und ihre bevorzugten Alternativen integriert sind.  
  
|Veraltete Bezeichnung|Bevorzugter Begriff|  
|-------------------|--------------------|  
|werden nicht|AreNot|  
|Cancelled|Canceled|  
|Kann nicht|Nicht möglich|  
|ComPlus|EnterpriseServices|  
|Testfalldaten|CouldNot|  
|Didnt|DidNot|  
|Nicht|DoesNot|  
|Dont|DoNot|  
|Flag oder Flags|Es gibt keine ersetzungsbegriff. Nicht verwenden.|  
|Hadnt|HadNot|  
|Noch nicht|HasNot|  
|noch nicht|HaveNot|  
|Indizes|Indizes|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Waren nicht|WereNot|  
|Empfängerseitige|WillNot|  
|Wouldnt|WouldNot|  
|Beschreibbare|Beschreibbare|  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff mit dem bevorzugten Begriff für die alternative.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und bezieht sich speziell auf dem ursprünglichen Begriff dem bevorzugten Begriff.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [Benennungswarnungen](../code-quality/naming-warnings.md)
