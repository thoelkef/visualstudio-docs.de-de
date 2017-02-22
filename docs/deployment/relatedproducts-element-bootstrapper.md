---
title: "&lt;RelatedProducts&gt;-Element (Bootstrapper) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.MissingDependency"
  - "MSBuild.GenerateBootstrapper.DuplicateItems"
  - "MSBuild.GenerateBootstrapper.IncludedProductIncluded"
  - "MSBuild.GenerateBootstrapper.DependencyNotFound"
  - "MSBuild.GenerateBootstrapper.PackageFileNotFound"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "<RelatedProducts>-Element [Bootstrapper]"
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;RelatedProducts&gt;-Element (Bootstrapper)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Das `RelatedProducts`\-Element definiert andere Produkte, die entweder vom aktuellen Produkt abhängig oder in diesem enthalten sind.  
  
## Syntax  
  
```  
<RelatedProducts>  
    <DependsOnProduct  
        Code  
    />  
    <EitherProducts>  
        <DependsOnProduct  
            Code  
        />  
    </EitherProducts>  
    <IncludesProduct  
        Code  
    />  
</RelatedProducts>  
```  
  
## Elemente und Attribute  
 Das `RelatedProducts`\-Element ist ein untergeordnetes Element des `Product`\-Elements.  Es sind keine Attribute vorhanden.  
  
## DependsOnProduct  
 Das `DependsOnProduct`\-Element gibt an, dass das aktuelle Produkt von dem benannten Produkt abhängig ist und das benannte Produkt daher vor dem aktuellen Produkt installiert werden muss.  Es ist ein untergeordnetes Element des `RelatedProducts`\-Elements.  Ein `RelatedProducts`\-Element kann über mindestens ein `DependsOnProduct`\-Element verfügen.  
  
 `DependsOnProduct` verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Code`|Der im `ProductCode`\-Attribut des `Product`\-Elements angegebene Codename des enthaltenen Produkts.  Weitere Informationen hierzu finden Sie unter [\<Product\>\-Element](../deployment/product-element-bootstrapper.md).|  
  
## EitherProducts  
 Das `EitherProducts`\-Element definiert 0 \(null\) oder mehr `DependsOnProduct`\-Elemente und verfügt über keine Attribute.  Mindestens ein `DependsOnProduct` in diesem Satz muss vor dem aktuellen Produkt installiert worden sein.  Ein `RelatedProducts`\-Element kann über 0 \(null\) oder mehrere `EitherProducts`\-Elemente verfügen.  
  
## IncludesProduct  
 Das `IncludesProduct`\-Element gibt an, dass ein Produkt in der aktuellen Installation enthalten ist und nicht separat installiert werden muss.  Es ist ein untergeordnetes Element des `RelatedProducts`\-Elements.  Ein `RelatedProducts`\-Element kann über mindestens ein `IncludesProduct`\-Element verfügen.  
  
 `IncludesProduct` verfügt über das folgende Attribut.  
  
|Attribut|Beschreibung|  
|--------------|------------------|  
|`Code`|Der im `ProductCode`\-Attribut des `Product`\-Elements angegebene Codename des enthaltenen Produkts.  Weitere Informationen hierzu finden Sie unter [\<Product\>\-Element](../deployment/product-element-bootstrapper.md).|  
  
## Beispiel  
 Im folgenden Codebeispiel wird angegeben, dass Microsoft Installer mit [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] installiert wird und daher nicht separat installiert werden muss.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## Siehe auch  
 [\<Product\>\-Element](../deployment/product-element-bootstrapper.md)