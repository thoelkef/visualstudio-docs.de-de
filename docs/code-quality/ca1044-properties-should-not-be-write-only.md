---
title: "CA1044: Eigenschaften sollten nicht lesegeschützt sein | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PropertiesShouldNotBeWriteOnly
- CA1044
helpviewer_keywords:
- CA1044
- PropertiesShouldNotBeWriteOnly
ms.assetid: 8386bf3a-b161-4841-bf8b-92591595aea9
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: cdb3ac5479193236b146c7c2607e5a27727695a3
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/22/2017
---
# <a name="ca1044-properties-should-not-be-write-only"></a>CA1044: Eigenschaften sollten nicht lesegeschützt sein
|||  
|-|-|  
|TypeName|PropertiesShouldNotBeWriteOnly|  
|CheckId|CA1044|  
|Kategorie|Microsoft.Design|  
|Unterbrechende Änderung|Breaking|  
  
## <a name="cause"></a>Ursache  
 Die öffentliche oder geschützte Eigenschaft verfügt über einen Set-Accessor, jedoch verfügt nicht über einen Get-Accessor.  
  
## <a name="rule-description"></a>Regelbeschreibung  
 Abrufen Geben Sie Accessoren Lesezugriff auf eine Eigenschaft und gewähren Sie Set-Accessoren Schreibzugriff. Obwohl eine schreibgeschützte Eigenschaft akzeptabel und oft erforderlich ist, verhindern die Entwurfsrichtlinien die Verwendung von Eigenschaften, die nur geschrieben werden können. Dies ist, da einen Benutzer einen Wert festlegen und dann verhindert, dass des Benutzers anzeigen des Werts kein Sicherheit geboten. Außerdem kann der Zustand freigegebener Objekte ohne Lesezugriff nicht angezeigt werden, wodurch ihre Nützlichkeit eingeschränkt wird.  
  
## <a name="how-to-fix-violations"></a>Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Get-Accessor der Eigenschaft. Auch wenn das Verhalten einer nur-Schreiben Eigenschaft erforderlich ist, sollten Sie konvertieren diese Eigenschaft auf eine Methode.  
  
## <a name="when-to-suppress-warnings"></a>Wann sollten Warnungen unterdrückt werden?  
 Es wird dringend empfohlen, dass Sie keine Warnung dieser Regel unterdrücken.  
  
## <a name="example"></a>Beispiel  
 Im folgenden Beispiel `BadClassWithWriteOnlyProperty` ist ein Typ mit nur-Schreiben-Eigenschaft. `GoodClassWithReadWriteProperty`enthält den korrigierten Code.  
  
 [!code-vb[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/VisualBasic/ca1044-properties-should-not-be-write-only_1.vb)]
 [!code-csharp[FxCop.Design.PropertiesNotWriteOnly#1](../code-quality/codesnippet/CSharp/ca1044-properties-should-not-be-write-only_1.cs)]