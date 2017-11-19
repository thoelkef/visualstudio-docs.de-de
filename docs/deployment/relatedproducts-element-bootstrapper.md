---
title: '&lt;RelatedProducts&gt; Element (Bootstrapper) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-deployment
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MSBuild.GenerateBootstrapper.MissingDependency
- MSBuild.GenerateBootstrapper.DuplicateItems
- MSBuild.GenerateBootstrapper.IncludedProductIncluded
- MSBuild.GenerateBootstrapper.DependencyNotFound
- MSBuild.GenerateBootstrapper.PackageFileNotFound
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords: <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: "12"
author: stevehoag
ms.author: shoag
manager: wpickett
ms.openlocfilehash: 4fa304f787c954b9ee89878e792e6f543f344f60
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/27/2017
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; Element (Bootstrapper)
Die `RelatedProducts` -Element definiert, andere Produkte, die entweder hängen davon ab, oder in das aktuelle Produkt enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
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
  
## <a name="elements-and-attributes"></a>Elemente und Attribute  
 Die `RelatedProducts` Element ist ein untergeordnetes Element von der `Product` Element. Es wurden keine Attribute.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Die `DependsOnProduct` -Element gibt an, dass das benannte Produkt das aktuelle Produkt abhängt und dass das benannte Produkt, die vor dem aktuellen Knoten installiert werden soll. Es ist ein untergeordnetes Element von der `RelatedProducts` Element. Ein `RelatedProducts` Element möglicherweise eine oder mehrere `DependsOnProduct` Elemente.  
  
 `DependsOnProduct`hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, entsprechend den Angaben von der `ProductCode` Attribut von der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Die `EitherProducts` -Element definiert, NULL oder mehr `DependsOnProduct` Elemente, und weist keine Attribute. Mindestens ein `DependsOnProduct` in dieser Gruppe müssen installiert werden, bevor das aktuelle Produkt. Ein `RelatedProducts` haben Element 0 (null) oder mehrere `EitherProducts` Elemente.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Die `IncludesProduct` -Element gibt an, dass ein Produkt in der aktuellen Installation enthalten ist, und keine separate Installation erfordert. Es ist ein untergeordnetes Element von der `RelatedProducts` Element. Ein `RelatedProducts` Element möglicherweise eine oder mehrere `IncludesProduct` Elemente.  
  
 `IncludesProduct`hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, entsprechend den Angaben von der `ProductCode` Attribut von der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt an, dass Microsoft Installer installiert ist die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], und eine separate Installation ist nicht erforderlich.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<Product >-Element](../deployment/product-element-bootstrapper.md)