---
title: "CA1044: Eigenschaften sollten nicht lesegesch&#252;tzt sein | Microsoft Docs"
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
  - "PropertiesShouldNotBeWriteOnly"
  - "CA1044"
helpviewer_keywords: 
  - "CA1044"
  - "PropertiesShouldNotBeWriteOnly"
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1044: Eigenschaften sollten nicht lesegesch&#252;tzt sein
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Kategorie \(Category\)|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## Ursache  
 Die öffentliche oder geschützte Eigenschaft hat einen set\-Accessor, jedoch keinen get\-Accessor.  
  
## Regelbeschreibung  
 get\-Accessoren geben Lesezugriff auf eine Eigenschaft, set\-Accessoren geben Schreibzugriff.  Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können.  Grund hierfür ist, dass eine Benutzerberechtigung, die das Anzeigen eines Werts nicht gestattet, das Festlegen des Werts jedoch zulässt, keinerlei Sicherheit bietet.  Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie der Eigenschaft einen get\-Accessor hinzu.  Wenn das Verhalten einer lesegeschützten Eigenschaft benötigt wird, sollten Sie auch erwägen, diese Eigenschaft in eine Methode zu konvertieren.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Es wird dringend empfohlen, keine Warnung dieser Regel zu unterdrücken.  
  
## Beispiel  
 Im folgenden Beispiel ist `BadClassWithWriteOnlyProperty` ein Typ mit der Eigenschaft "lesegeschützt" festgelegt.  `GoodClassWithReadWriteProperty` enthält den korrigierten Code.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-cs[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]