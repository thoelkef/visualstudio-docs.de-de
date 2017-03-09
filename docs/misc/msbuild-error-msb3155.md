---
title: "MSBuild Error MSB3155 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3155
**MSBuild\-Fehler MSB3155: Das Element \<Paket\> konnte in \<Pfad\> nicht gefunden werden.**  
  
 Die Warnung wird ausgegeben, wenn ein Paket mit dem angegebenen <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> im Bootstrappercache nicht gefunden werden konnte.  
  
> [!NOTE]
>  Microsoft Data Access Components \(MDAC\) sind nicht mehr als Bootstrapperpaket enthalten.  Sie können von der [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676)\-Website heruntergeladen werden.  
  
### So beheben Sie diesen Fehler  
  
-   Entfernen Sie das Paket aus der Liste der zu installirenden Pakete, oder fügen Sie das Paket dem Cache hinzu.  Vergewissern Sie sich auch, dass das Manifest ordnungsgemäß formatiert ist und gültiger XML\-Code verwendet wird.  
  
## Siehe auch  
 [Referenz zum Produkt\- und Paketschema](../deployment/product-and-package-schema-reference.md)   
 [\<PackageFiles\>\-Element](../deployment/packagefiles-element-bootstrapper.md)   
 [Dialogfeld "Erforderliche Komponenten"](../ide/reference/prerequisites-dialog-box.md)   
 [Erstellen von Bootstrapperpaketen](../deployment/creating-bootstrapper-packages.md)