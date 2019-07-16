---
title: '&lt;RelatedProducts&gt; -Element (Bootstrapper) | Microsoft-Dokumentation'
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 42756b21e631ec14e9c590833f6f0e95a317cc22
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2019
ms.locfileid: "66747458"
---
# <a name="ltrelatedproductsgt-element-bootstrapper"></a>&lt;RelatedProducts&gt; -Element (Bootstrapper)
Die `RelatedProducts` -Element definiert, andere Produkte, die entweder hängen davon ab, oder sind in das aktuelle Produkt enthalten.

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
 Das folgende Codebeispiel gibt an, dass Microsoft Installer mit .NET Framework installiert ist, und eine separate Installation ist nicht erforderlich.

```xml
<RelatedProducts>
    <IncludesProduct Code="Microsoft.Windows.Installer.2.0" />
</RelatedProducts>
```

## <a name="see-also"></a>Siehe auch
- [\<Produkt >-Element](../deployment/product-element-bootstrapper.md)