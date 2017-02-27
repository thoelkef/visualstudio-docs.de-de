---
title: "&lt;Schedules&gt;-Element (Bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<Schedules>-Element [Bootstrapper]"
ms.assetid: 28d094cf-64f5-42b1-bd8a-3697082aab4f
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# &lt;Schedules&gt;-Element (Bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das `Schedules`\-Element enthält `Schedule`\-Elemente, mit denen bestimmte Zeitpunkte definiert werden, zu denen die vom `Command`\-Element definierten Befehle ausgeführt werden sollen.  
  
## Syntax  
  
```  
<Schedules>  
    <Schedule  
        Name  
    >  
        <BuildList />  
        <BeforePackage />  
        <AfterPackage />  
    </Schedule>  
</Schedules>  
```  
  
## Elemente und Attribute  
 Das `Schedules`\-Element ist ein untergeordnetes Element des `Product`\-Elements.  Jedes `Product`\-Element kann über höchstens ein `Schedules`\-Element verfügen.  Das `Schedules`\-Element weist keine Attribute auf.  
  
## Schedule  
 Das `Schedule`\-Element ist ein untergeordnetes Element des `Schedules`\-Elements.  Ein `Schedules`\-Element muss über mindestens ein `Schedule`\-Element verfügen.  
  
 `Schedule` verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Name`|Erforderlich.  Der Name des Schedule\-Elements.  Dieser entspricht der `ScheduleName`\-Eigenschaft des `Command`\-Elements.  Wenn ein `Command` auf den benannten Zeitplan verweist, wird er erst zu dem Zeitpunkt ausgeführt, der von diesem `Schedule`\-Element angegeben wird.  Zeitpläne können auch mit dem `FailIf`\-Element und dem `BypassIf`\-Element verknüpft werden, wodurch diese bedingten Tests ausschließlich nach dem angegebenen Zeitplan ausgeführt werden.  Weitere Informationen finden Sie unter [\<Commands\>\-Element](../deployment/commands-element-bootstrapper.md).|  
  
 Ein bestimmtes `Schedule`\-Element verfügt möglicherweise genau über eines der folgenden untergeordneten Elemente.  
  
## BuildList  
 Das `BuildList`\-Element weist das Installationsprogramm an, einen Befehl sofort nach dem Start der Bootstrapperanwendung auszuführen.  
  
## BeforePackage  
 Das `BeforePackage`\-Element weist das Installationsprogramm an, einen Befehl vor der Installation des angegebenen Pakets auszuführen.  
  
## AfterPackage  
 Das `AfterPackage`\-Element weist das Installationsprogramm an, einen Befehl nach der Installation des angegebenen Pakets auszuführen.  
  
## Siehe auch  
 [\<Product\>\-Element](../deployment/product-element-bootstrapper.md)   
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)