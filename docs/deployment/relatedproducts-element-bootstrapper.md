---
title: '&lt;RelatedProducts&gt; Element (Bootstrapper) | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-deployment
ms.topic: conceptual
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
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5701b88f3942301c8fdb6d674fc323e62a93589b
ms.sourcegitcommit: 1b9c1e333c2f096d35cfc77e846116f8e5054557
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2018
ms.locfileid: "34815456"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; Element (Bootstrapper)
Die `RelatedProducts` -Element definiert, andere Produkte, die entweder hängen davon ab, oder in das aktuelle Produkt enthalten sind.  
  
## <a name="syntax"></a>Syntax  
  
```xml  
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
  
 `DependsOnProduct` hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, entsprechend den Angaben von der `ProductCode` Attribut von der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="eitherproducts"></a>EitherProducts  
 Die `EitherProducts` -Element definiert, NULL oder mehr `DependsOnProduct` Elemente, und weist keine Attribute. Mindestens ein `DependsOnProduct` in dieser Gruppe müssen installiert werden, bevor das aktuelle Produkt. Ein `RelatedProducts` haben Element 0 (null) oder mehrere `EitherProducts` Elemente.  
  
## <a name="includesproduct"></a>IncludesProduct  
 Die `IncludesProduct` -Element gibt an, dass ein Produkt in der aktuellen Installation enthalten ist, und keine separate Installation erfordert. Es ist ein untergeordnetes Element von der `RelatedProducts` Element. Ein `RelatedProducts` Element möglicherweise eine oder mehrere `IncludesProduct` Elemente.  
  
 `IncludesProduct` hat das folgende Attribut.  
  
|Attribut|Beschreibung|  
|---------------|-----------------|  
|`Code`|Der Code-Name des Produkts enthalten, entsprechend den Angaben von der `ProductCode` Attribut von der `Product` Element. Weitere Informationen finden Sie unter [ \<Product >-Element](../deployment/product-element-bootstrapper.md).|  
  
## <a name="example"></a>Beispiel  
 Das folgende Codebeispiel gibt an, dass Microsoft Installer installiert ist die [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], und eine separate Installation ist nicht erforderlich.  
  
```xml  
<RelatedProducts>  
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />  
</RelatedProducts>  
```  
  
## <a name="see-also"></a>Siehe auch  
 [\<Product >-Element](../deployment/product-element-bootstrapper.md)