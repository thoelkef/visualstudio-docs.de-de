---
title: "CA1726: Bevorzugte Begriffe verwenden | Microsoft Docs"
ms.custom: ""
ms.date: "12/02/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
caps.handback.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1726: Bevorzugte Begriffe verwenden
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Kategorie \(Category\)|Microsoft.Naming|  
|Unterbrechende Änderung|Unterbrechend – Wenn für Assemblys ausgelöst<br /><br /> Nicht unterbrechend – Wenn für Typparameter ausgelöst|  
  
## Ursache  
 Der Name eines extern sichtbaren Bezeichners schließt einen Begriff ein, für den ein alternativer, bevorzugter Begriff vorhanden ist.  Alternativ schließt der Name den Begriff Flag oder Flags ein.  
  
## Regelbeschreibung  
 Diese Regel analysiert einen Bezeichner auf Token.  Jedes einzelne Token und jede Kombination aus zwei zusammenhängenden Token wird mit Begriffen verglichen, die in die Regel und den Deprecated\-Abschnitt von benutzerdefinierten Wörterbüchern integriert sind.  In der folgenden Tabelle werden die in die Regel integrierten Begriffe und die zugehörigen bevorzugten Alternativen angezeigt.  
  
|Veralteter Begriff|Bevorzugter Begriff|  
|------------------------|-------------------------|  
|Arent|AreNot|  
|Cancelled|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag oder Flags|Es gibt keinen Ersatzausdruck.  Nicht verwenden.|  
|Hadnt|HadNot|  
|Hasn’t|HasNot|  
|Havent|HaveNot|  
|Indices|Indizes|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, ersetzen Sie den Begriff durch den bevorzugten alternativen Begriff.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Unterdrücken Sie eine Warnung dieser Regel nur dann, wenn der Name des Bezeichners absichtlich und ausdrücklich auf den ursprünglichen Begriff verweist und nicht auf den bevorzugten Begriff.  
  
## Verwandte Regeln  
 [Benennungswarnungen](../code-quality/naming-warnings.md)