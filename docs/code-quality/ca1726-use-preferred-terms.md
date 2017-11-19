---
title: 'CA1726: Bevorzugte Begriffe verwenden | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Bevorzugte Begriffe verwenden
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Kategorie|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst|  
  
## <a name="cause"></a>Ursache  
 Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist. Alternativ können Sie enthält den Namen den Begriff Flag oder Flags.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Diese Regel analysiert einen Bezeichner in Token. Jedes einzelne Token und jede Kombination aus zwei zusammenhängenden token wird mit Begriffen verglichen, die in der Regel und den Deprecated-Abschnitt von benutzerdefinierten Wörterbüchern integriert sind. Die folgende Tabelle zeigt die Begriffe, die in der Regel und ihrer bevorzugten Alternativen integriert werden.  
  
|Veraltete Bezeichnung|Bevorzugter Begriff|  
|-------------------|--------------------|  
|werden nicht|Nicht|  
|abgebrochen|Canceled|  
|Nicht möglich|Kann nicht|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Nicht|Wiederherstellungsdienst|  
|Nicht|Zu|  
|Flag oder Flags|Es gibt keine ersetzungsbegriff. Nicht verwenden.|  
|hadn't|HadNot|  
|Noch nicht|HasNot|  
|dies nicht getan haben|HaveNot|  
|Indizes|Indexes|  
|ist nicht|IsNot|  
|Anmeldung|Anmeldung|  
|Abmelden|Abmelden|  
|Shouldnt|ShouldNot|  
|Anmelden|Anmelden|  
|Genehmigung|Abmelden|  
|Wasnt|WasNot|  
|datenträgerressourceneinstellungen wurden nicht|Netzwerkparameter|  
|Nicht möglich|WillNot|  
|Würde nicht|WouldNot|  
|Beschreibbare|beschreibbare|  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff mit den bevorzugten Alternativen Begriff aus.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur, wenn der Name des Bezeichners beabsichtigt ist und bezieht sich speziell auf den ursprünglichen Begriff statt dem bevorzugten Begriff.  
  
## <a name="related-rules"></a>Verwandte Regeln  
 [Benennungswarnungen](../code-quality/naming-warnings.md)