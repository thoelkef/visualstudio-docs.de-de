---
title: 'CA1726: Bevorzugte Begriffe verwenden | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: b13c43a563a158a2eeb8484e29810c5b91d110aa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510957"
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Dokumentation für Visual Studio 2017 finden Sie unter [CA1726: Bevorzugte Begriffe verwenden](https://docs.microsoft.com/visualstudio/code-quality/ca1726-use-preferred-terms) auf docs.microsoft.com.  
  
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
|werden nicht|Nicht|  
|Abgebrochen|Canceled|  
|Kann nicht|Nicht möglich|  
|ComPlus|EnterpriseServices|  
|Testfalldaten|CouldNot|  
|Didnt|DidNot|  
|Nicht|Nicht|  
|Nicht erforderlich|Zu|  
|Flag oder Flags|Es gibt keine ersetzungsbegriff. Nicht verwenden.|  
|noch nicht|HadNot|  
|Noch nicht|HasNot|  
|noch nicht|HaveNot|  
|Indizes|Indexes|  
|ist nicht|IsNot|  
|Anmeldung|Anmeldung|  
|Abmelden|Abmelden|  
|Shouldnt|ShouldNot|  
|Anmelden|Anmeldung|  
|Durch die qualitätssicherung|Abmelden|  
|Wasnt|WasNot|  
|Waren nicht|Netzwerkparameter|  
|Empfängerseitige|WillNot|  
|Würde nicht|WouldNot|  
|Beschreibbare|Beschreibbare|  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff mit dem bevorzugten Begriff für die alternative.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und bezieht sich speziell auf dem ursprünglichen Begriff dem bevorzugten Begriff.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [Benennungswarnungen](../code-quality/naming-warnings.md)

