---
title: '&lt;RelatedProducts&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-deployment
ms.tgt_pltfrm: ''
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
helpviewer_keywords:
- <RelatedProducts> element [bootstrapper]
ms.assetid: bf152712-4c1e-48bd-9b7f-311cf0fdb832
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: wpickett
ms.openlocfilehash: ee65c4e4cacd4680256e34583559d74935a89e3b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/22/2018
ms.locfileid: "47510476"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; -Element (Bootstrapper)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Die neueste Version dieses Themas finden Sie unter [ &lt;RelatedProducts&gt; -Element (Bootstrapper)](https://docs.microsoft.com/visualstudio/deployment/relatedproducts-element-bootstrapper).  
  
Die `RelatedProducts` -Element definiert, andere Produkte, die entweder hängen davon ab, oder sind in das aktuelle Produkt enthalten.  
  
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
 Die `RelatedProducts` Element ist ein untergeordnetes Element des der `Product` Element. Es besitzt keine Attribute.  
  
## <a name="dependsonproduct"></a>DependsOnProduct  
 Die `DependsOnProduct` -Element gibt an, dass das benannte Produkt das aktuelle Produkt abhängig und das benannte Produkt vor dem aktuellen Knoten installiert werden soll. Es ist ein untergeordnetes Element des der `RelatedProducts` Element. Ein `RelatedProducts` Element möglicherweise eine oder mehrere `DependsOnProduct` Elemente.  
  
 `DependsOnProduct` weist das folgende Attribut an.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, laut der `ProductCode` Attribut der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Die `EitherProducts` -Element definiert NULL oder mehr `DependsOnProduct` Elemente, und weist keine Attribute. Mindestens ein `DependsOnProduct` in diesem Satz müssen vor dem aktuellen Produkt installiert werden. Ein `RelatedProducts` haben Element 0 (null) oder mehrere `EitherProducts` Elemente.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Die `IncludesProduct` -Element gibt an, dass ein Produkt in der aktuellen Installation enthalten ist, und eine separate Installation ist nicht erforderlich. Es ist ein untergeordnetes Element des der `RelatedProducts` Element. Ein `RelatedProducts` Element möglicherweise eine oder mehrere `IncludesProduct` Elemente.  
  
 `IncludesProduct` weist das folgende Attribut an.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, laut der `ProductCode` Attribut der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt an, mit der Microsoft-Installer installiert die [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], und eine separate Installation ist nicht erforderlich.  
  
```  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<Produkt >-Element](../deployment/product-element-bootstrapper.md)



