---
title: "CA1409: F&#252;r COM sichtbare Typen m&#252;ssen erstellt werden k&#246;nnen | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
helpviewer_keywords: 
  - "ComVisibleTypesShouldBeCreatable"
  - "CA1409"
ms.assetid: 9f59569b-de15-4a38-b7cb-cff152972243
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1409: F&#252;r COM sichtbare Typen m&#252;ssen erstellt werden k&#246;nnen
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ComVisibleTypesShouldBeCreatable|  
|CheckId|CA1409|  
|Kategorie \(Category\)|Microsoft.Interoperability|  
|Unterbrechende Änderung|Nicht unterbrechend|  
  
## Ursache  
 Ein Verweistyp, der speziell als für COM \(Component Object Model\) sichtbar gekennzeichnet ist, enthält einen öffentlichen parametrisierten Konstruktor, jedoch keinen öffentlichen \(parameterlosen\) Standardkonstruktor.  
  
## Regelbeschreibung  
 Ein Typ ohne öffentlichen Standardkonstruktor kann nicht von COM\-Clients erstellt werden.  COM\-Clients können dennoch auf den Typ zugreifen, wenn der Typ auf andere Weise erstellt und an den Client übergeben werden kann, z. B. durch den Rückgabewert eines Methodenaufrufs.  
  
 Die Regel ignoriert Typen, die von <xref:System.Delegate?displayProperty=fullName> abgeleitet sind.  
  
 Standardmäßig sind folgende Programmierelemente für COM sichtbar: Assemblys, öffentliche Typen, öffentliche Instanzmember in öffentlichen Typen und alle Member öffentlicher Werttypen.  
  
## Behandeln von Verstößen  
 Um einen Verstoß gegen diese Regel zu beheben, fügen Sie einen Standardkonstruktor hinzu, oder entfernen Sie das <xref:System.Runtime.InteropServices.ComVisibleAttribute?displayProperty=fullName> von dem Typ.  
  
## Wann sollten Warnungen unterdrückt werden?  
 Eine Warnung dieser Regel kann gefahrlos unterdrückt werden, wenn es andere Möglichkeiten gibt, das Objekt zu erstellen und an den COM\-Client zu übergeben.  
  
## Verwandte Regeln  
 [CA1017: Assemblys mit ComVisibleAttribute markieren](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)  
  
## Siehe auch  
 [Qualifying .NET Types for Interoperation](../Topic/Qualifying%20.NET%20Types%20for%20Interoperation.md)   
 [Interoperating with Unmanaged Code](../Topic/Interoperating%20with%20Unmanaged%20Code.md)